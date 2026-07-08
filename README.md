# MAISON AURA — Tienda de moda de lujo

Web de marca de ropa de alta costura: hero con vestido 3D de partículas, tienda con
carrito de compra, lookbook, atelier 3D interactivo, journal y FAQ. Un solo archivo
HTML sin dependencias — funciona en cualquier hosting estático.

**Web en vivo:** https://tizilongo666-ctrl.github.io/mi1erproyecto/

---

## 📁 Qué contiene el proyecto

| Archivo | Qué es |
|---|---|
| `index.html` | Toda la web: diseño, tienda, carrito y 3D |
| `legal.html` | Aviso legal, privacidad, cookies y condiciones de venta |
| `404.html` | Página de error elegante |
| `robots.txt` / `sitemap.xml` | SEO para Google |

## ✏️ Cómo editar los productos

Abre `index.html` y busca `PRODUCTS` (usa Ctrl+F). Cada producto es una línea:

```js
{id:"eclipse", n:"Vestido Éclipse", cat:"vestidos", fab:"Seda charmeuse · negro tinta",
 p:1890, img:IMG("1539109136881-3be0616acf4b"), d:"Descripción larga..."},
```

- `n` = nombre · `p` = precio en euros · `cat` = categoría (`vestidos`, `abrigos`, `sastreria`, `punto`) · `d` = descripción de la vista rápida.
- `img`: acepta cualquier URL de imagen. `IMG("...")` usa fotos de Unsplash;
  para una foto propia pon `img:"https://tudominio.com/foto.jpg"` o súbela al repo
  (`assets/foto.jpg`) y pon `img:"assets/foto.jpg"`.
- Para añadir un producto, duplica una línea y cambia el `id` (debe ser único).
- Guarda, haz commit y push: la web se actualiza sola en 1–2 minutos.

## 💳 Activar el pago real (Stripe)

El checkout actual es una simulación. Para cobrar de verdad:

1. Crea una cuenta gratuita en [stripe.com](https://stripe.com) (necesita cuenta bancaria del negocio).
2. En el panel de Stripe: **Payment Links → Nuevo enlace de pago**, añade los productos con sus precios.
3. Copia la URL (`https://buy.stripe.com/...`).
4. En `index.html`, busca `PAYMENT_LINK = ""` y pega la URL entre las comillas.

Con eso, el botón "Finalizar compra" llevará al pago real. Comisión de Stripe: ~1,5 % + 0,25 € por venta en tarjetas europeas. Sin cuota mensual.

## 🌐 Conectar un dominio propio

1. Compra el dominio (Cloudflare Registrar, Namecheap o Porkbun; ~10–15 €/año).
2. En el panel DNS del dominio crea:
   - Registro **A** en `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Registro **CNAME** en `www` → `tizilongo666-ctrl.github.io`
3. En GitHub: **Settings → Pages → Custom domain** → escribe el dominio → Save.
4. Marca **Enforce HTTPS** cuando se active (tarda unos minutos).
5. Actualiza las URLs `tizilongo666-ctrl.github.io/mi1erproyecto` por el dominio nuevo en:
   `index.html` (etiquetas `canonical` y `og:`), `robots.txt`, `sitemap.xml` y el enlace del `404.html`.

## ⚖️ Antes de empezar a vender

- En `legal.html`, sustituye los campos dorados `[NOMBRE...]`, `[NIF...]`, `[DIRECCIÓN...]`,
  `[EMAIL...]` por los datos reales del titular, y borra el recuadro de nota.
- Da de alta la web en [Google Search Console](https://search.google.com/search-console)
  y envía el `sitemap.xml` para aparecer en Google.

## 🤝 Checklist de traspaso a un comprador

- [ ] Transferir el repositorio: **Settings → General → Transfer ownership** (o subir el código a la cuenta GitHub del comprador y reactivar Pages allí).
- [ ] Dominio registrado a nombre del comprador (o transferencia de registrador).
- [ ] Cuenta de Stripe propia del comprador con su banco (el `PAYMENT_LINK` se cambia en 1 minuto).
- [ ] Datos del titular actualizados en `legal.html`.
- [ ] Email corporativo del dominio (Zoho Mail gratis o Google Workspace).
- [ ] Entregar este README como manual de uso.
