# Loginco Transporte — Sitio Web Corporativo

Sitio web estático de una sola página para **Loginco Transporte**, empresa especializada en carga contenerizada FCL/LCL, transporte local y larga distancia, y logística corporativa en México.

**URL de producción:** https://transporte.loginco.com.mx

---

## Estructura del proyecto

```
Transporte/
├── index.html        # Sitio completo (HTML + CSS + JS inline)
├── sitemap.xml       # Sitemap para motores de búsqueda
├── robots.txt        # Directivas de indexación
└── img/
    ├── Isotipo.png          # Favicon / ícono de la marca
    ├── Isotipo.svg          # Ícono vectorial
    ├── Logotipo.png         # Logo completo (header)
    ├── LogotipoFooter.png   # Logo para footer
    └── og-image.jpg         # Imagen Open Graph 1200×630 px (pendiente de crear)
```

## Ejecutar localmente

```bash
python3 -m http.server 8000
```

Abre http://localhost:8000 en el navegador. No requiere build ni instalación de dependencias.

---

## Stack tecnológico

| Tecnología | Versión | Uso |
|-----------|---------|-----|
| HTML5 | — | Estructura y semántica |
| Tailwind CSS | v3 (CDN) | Utilidades de estilos |
| Font Awesome | 6.4.0 (CDN) | Iconografía |
| Google Fonts | — | Montserrat (títulos), DM Sans (cuerpo) |
| JavaScript | ES6 vanilla | Menú móvil, validación, animaciones scroll |

> El sitio requiere conexión a internet para cargar fuentes e iconos desde CDN.

---

## Secciones del sitio

| # | Sección | ID ancla |
|---|---------|----------|
| 1 | Header / Navbar sticky | — |
| 2 | Hero con estadísticas | `#inicio` |
| 3 | Nosotros (misión, visión, stats) | `#nosotros` |
| 4 | Servicios (6 cards: FCL, LCL, local, larga distancia, corporativo, almacenaje) | `#servicios` |
| 5 | Flota (3 tipos de unidad) | `#flota` |
| 6 | Cobertura nacional | `#cobertura` |
| 7 | Contacto / Formulario de cotización | `#contacto` |
| 8 | Footer | — |

---

## Tokens de diseño

```css
--primary-dark:  #00018d   /* Azul oscuro — color principal de marca */
--primary-mid:   #3839bc   /* Índigo medio */
--primary-light: #7e7fb7   /* Morado claro */
--accent:        #08b8b5   /* Teal — botones CTA */
--accent-dark:   #069e9b   /* Teal hover */
```

**Fuentes:**
- Títulos: `Montserrat` (pesos 600–900)
- Cuerpo: `DM Sans` (pesos 300–700)

---

## SEO

El sitio incluye:

- Meta `description`, `keywords`, `robots: index, follow`
- `<link rel="canonical" href="https://transporte.loginco.com.mx/">`
- **Open Graph** completo (título, descripción, imagen 1200×630, URL, locale `es_MX`)
- **Twitter/X Cards** (`summary_large_image`)
- **Schema.org JSON-LD** con `@graph`:
  - `FreightForwarder + LocalBusiness` con dirección, teléfono, horario, área de servicio
  - `OfferCatalog` con los 6 servicios como entidades `Offer > Service`
  - `AggregateRating` (4.9/5 basado en +500 clientes)
  - `WebSite` vinculado a la organización
- `sitemap.xml` referenciado en `robots.txt`

### Imagen OG pendiente

Crear `img/og-image.jpg` de **1200 × 630 px** antes de publicar. Sin ella, los previews en WhatsApp, LinkedIn y Facebook mostrarán imagen rota.

---

## Formulario de contacto

El formulario es **solo frontend** — no envía datos a ningún servidor. Al enviarse muestra un mensaje de éxito simulado.

Para integrarlo con un backend, opciones recomendadas:

| Opción | Descripción |
|--------|-------------|
| [Formspree](https://formspree.io) | Sin backend propio, gratis hasta 50 envíos/mes |
| [EmailJS](https://www.emailjs.com) | Envío directo desde JS, sin servidor |
| Webhook propio | `fetch` POST al endpoint del CRM o sistema interno |

---

## Pendientes antes de producción

- [ ] Crear `img/og-image.jpg` (1200 × 630 px)
- [ ] Reemplazar teléfono placeholder en JSON-LD (`+52-753-000-0000`) con el número real
- [ ] Agregar dirección exacta (calle y número) en JSON-LD `streetAddress`
- [ ] Configurar DNS del subdominio `transporte.loginco.com.mx`
- [ ] Verificar dominio en [Google Search Console](https://search.google.com/search-console) y enviar el sitemap
- [ ] Integrar formulario con backend de email o CRM
- [ ] (Opcional) Reclamar y optimizar Google Business Profile en Lázaro Cárdenas

---

## Notas de desarrollo

- Todo el CSS personalizado y el JS están **inline en `index.html`** — no hay archivos separados.
- Las imágenes están en `img/` — son los únicos assets locales.
- Para producción, considerar descargar las dependencias CDN (Tailwind, Font Awesome, Google Fonts) para funcionamiento offline y mejor rendimiento.
