# Ember & Oak

A three-page marketing site for a wood-fire restaurant, with a full menu page and a reservation form that composes an email.

**Live:** https://ember-oak-gold-gamma.vercel.app

Source code is in this repo — hand-written HTML/CSS/vanilla JS, no build step. Serve the folder locally (see below).

## About

Ember & Oak is a demo restaurant site: a three-page marketing build for a wood-fire kitchen, with a homepage, a complete menu organised into courses, and a contact/reservation page. It is a static build with no backend — the reservation form reads the visitor's input and hands it to their mail client as a pre-filled message.

## Tech stack

| | |
|---|---|
| Markup | HTML5, three pages |
| Styling | `css/style.css`, CSS custom properties, `clamp()` type scale |
| Script | `js/main.js` — vanilla JS, one IIFE, no dependencies |
| Fonts | Google Fonts |
| Images | 8 local JPEGs in `img/` |
| Build | None. No `package.json`, no dependencies |
| Hosting | Vercel, static hosting |

## Features

Everything below is implemented in the repo.

- **Three pages** — `index.html`, `menu.html`, `contact.html` — sharing one stylesheet and one script.
- **Reservation form** (`#book`) with name, phone, guests, date and note fields; on submit it builds a formatted reservation request and opens the visitor's mail client with the subject and body filled in, then disables the button and reveals a confirmation note. Client-side `required` attributes handle the empty-field case.
- **Menu page** — full menu grouped into four sections (starters, from the fire, karahi & mains, desserts and drinks) with prices in PKR.
- **Mobile navigation** — hamburger toggle that flips `aria-expanded` and closes automatically when a link is tapped.
- **Page-load splash** — a `#sp` overlay is removed shortly after load.
- **Scroll reveal** — elements marked `.rise` fade in via `IntersectionObserver` (threshold 0.15) and unobserve once shown.
- **Header shadow on scroll** past 8px, giving the sticky header depth.
- **Responsive** — breakpoints at 900px and 520px.
- Consistent header/footer with opening hours shown on every page.

## Project structure

```
.
├── index.html        # homepage
├── menu.html         # full menu
├── contact.html      # contact + reservation form
├── css/
│   └── style.css
├── js/
│   └── main.js
├── img/              # hero.jpg, grill.jpg, steak.jpg, kebab.jpg, karahi.jpg, bowl.jpg, plate.jpg, interior.jpg
├── favicon.svg
├── .gitignore        # ignores .vercel
└── .vercel/          # Vercel project link (projectName: ember-oak)
```

## Local preview

No install step. Because the pages link each other and reference `css/` and `js/` by relative path, serve them over HTTP rather than opening the file directly:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Notes

- **Practice build.** The restaurant, its address, hours and menu are sample content written for the demo — not a real business and not a delivered client project.
- The reservation form has no server behind it; delivery is via `mailto:`. Swapping it for a real endpoint means replacing the `mailto:` branch in `js/main.js`.
