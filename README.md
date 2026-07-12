# DevConf 2026 — Landing Page

A single-page conference landing site built with plain HTML and CSS. Covers navigation, hero banner, speaker highlights, pricing tiers, an FAQ accordion (markup + styles only), and a footer.

## Preview Sections

- **Navbar** — logo, nav links, "Register Now" CTA
- **Hero** — headline, subtext, CTA button, full-bleed background image
- **Speakers** — 4-card grid with photo, category tag, name, role
- **Pricing** — Standard / Pro / Team tiers with feature lists
- **FAQ** — accordion-style question list
- **Footer** — logo, social icons, copyright, legal links

## Tech Stack

- HTML5
- CSS3 (custom, no framework)
- [Font Awesome 6.5.1](https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css) — social icons
- Google Fonts — `Arimo`, `Inter`

## Project Structure

```
.
├── index.html
├── style.css
└── assets/          # referenced but not included — see "Known Issues"
    ├── logo.png
    ├── footer-logo.png
    ├── banner.jpg
    ├── andrej.png
    ├── gary.png
    ├── demis.png
    └── mustafa.png
```

## Running Locally

No build step. Clone it and open it.

```bash
git clone <your-repo-url>
cd devconf-2026
```

Then either:
- Open `index.html` directly in a browser, or
- Serve it locally for correct relative-path behavior:

```bash
npx serve .
# or
python3 -m http.server 8080
```

## Known Issues / TODO

Straight talk — this is a v1 landing page, not production-ready. Fix these before shipping:

1. **`assets/` folder is missing.** `index.html` references 7 images (`logo.png`, `banner.jpg`, 4 speaker photos, `footer-logo.png`) that don't exist in this repo yet. Add them or every image breaks.
2. **FAQ accordion has no JavaScript.** The CSS has `.faq-item.active` states fully styled, but there's no script toggling that class on click. Right now the questions don't open. Needs a `script.js` with a click listener per `.faq-question`.
3. **Inline style in footer.** `style="margin-left: 1040px; display: flex; gap: 15px;"` in `index.html` — hardcoded pixel margin, will break on any screen narrower than ~1040px. Move it to CSS and use flex/justify instead of a magic-number margin.
4. **No responsive breakpoints.** Zero media queries in `style.css`. The 4-speaker grid, 3-card pricing row, and fixed-width footer layout will all break on tablet/mobile.
5. **Typos in class names and copy** — `poient` (should be `point`), `techear section` (comment, should be `speaker`), `banar section` (comment, should be `banner`), `"Cloud & DevO psL"` in Demis Hassabis's card (garbled, should probably be `Cloud & DevOps`), `srcton` (comment, should be `section`). Cosmetic, but sloppy for anything going in front of a client.
6. **Empty `alt` attributes** on every `<img>` tag. Bad for accessibility and SEO — fill these in with real descriptions.
7. **Duplicate `<link rel="preconnect">` tags** for Google Fonts in the `<head>` — repeated twice for no reason, delete the redundant pair.
8. **`#hr` used as an ID selector on multiple elements** (`<aside id="hr">` appears 3+ times in pricing cards). IDs must be unique — rename to a class.

## License

Add a license of your choice (MIT is the standard default for portfolio projects).
