# Novedades Rizo — paquete PWA y guía Android

## Qué contiene
- `index.html`: tienda adaptada desde el sitio actual.
- `manifest.webmanifest`: nombre, colores, iconos y modo instalable.
- `sw.js`: caché básica para mejorar la apertura posterior.
- `icons/`: iconos para Android y navegadores.

## Publicar gratis en Internet
La tienda debe estar alojada en una URL HTTPS pública para que la instalación PWA y Trusted Web Activity funcionen. Puedes usar un alojamiento estático gratuito como GitHub Pages o Cloudflare Pages. Sube el contenido de esta carpeta (no la carpeta contenedora) al proyecto. Después prueba la URL en Android/Chrome.

## Antes de vender
1. En `index.html`, busca `const phone="521XXXXXXXXXX"` y reemplázalo con el número de WhatsApp real, con código de país y solo dígitos.
2. Cambia los productos, precios y descripciones de ejemplo por información real.
3. El botón de tarjeta solo muestra una nota: no cobra. Para cobrar, integra una pasarela real (por ejemplo Mercado Pago) y usa su checkout seguro.
4. Añade datos de contacto, políticas de privacidad, devoluciones, envíos y términos de compra adecuados a tu negocio.

## Crear la app Android para Google Play (después de alojar la web)
Necesitarás una URL HTTPS pública propia y verificar que te pertenece. Con Node.js instalado, abre una terminal:

```bash
npm install -g @bubblewrap/cli
bubblewrap init --manifest=https://TU-DOMINIO/manifest.webmanifest
bubblewrap build
```

Sigue el asistente, revisa el nombre/paquete, iconos y firma. Para Google Play normalmente se entrega el archivo `.aab` que genere la herramienta; confirma el archivo de salida que muestre tu versión de Bubblewrap. Configura Digital Asset Links en `https://TU-DOMINIO/.well-known/assetlinks.json` usando el nombre de paquete y huella SHA-256 de la clave de firma correctos. Si usas firma de aplicaciones de Play, verifica la huella de la clave de firma de Play Console.

## Costes y requisitos
- Alojamiento estático: puede ser gratis.
- Google Play Console: la documentación oficial indica una tarifa única de registro de US$25; además, las cuentas personales nuevas pueden tener requisitos de prueba y verificación. La aprobación no está garantizada.
- No compartas tus contraseñas ni claves privadas de firma.

## Referencias oficiales
- Guía Android Trusted Web Activities: https://developer.android.com/develop/ui/views/layout/webapps/guide-trusted-web-activities-version2?hl=es-419
- Registro Play Console: https://support.google.com/googleplay/android-developer/answer/6112435?hl=es-419

{
  "id": "/",
  "name": "Novedades Rizo",
  "short_name": "Rizo",
  "description": "Tienda en línea de novedades, accesorios, tecnología, moda y hogar.",
  "lang": "es-MX",
  "start_url": "./",
  "scope": "./",
  "display": "standalone",
  "orientation": "portrait-primary",
  "background_color": "#fff9fd",
  "theme_color": "#743cff",
  "categories": [
    "shopping"
  ],
  "icons": [
    {
      "src": "icons/icon-192.png",
      "sizes": "192x192",
      "type": "image/png",
      "purpose": "any"
    },
    {
      "src": "icons/icon-512.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "any"
    },
    {
      "src": "icons/icon-512-maskable.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "maskable"
    }
  ]
}
