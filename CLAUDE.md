# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page website for Civil & Structural Engineering Company PLLC, owned by Russell S. Johnson P.E. The site is built with vanilla HTML5, CSS3, and JavaScript—no build system or package manager is used. All work stays within `index.html`; no separate pages are created.

**Domain:** civilstructuralengineers.com  
**Target Audience:** Local clients in Mesa, AZ seeking civil and structural engineering services

---

## Development Environment

### Local Development

Use **Live Server** (VSCode extension) to preview changes:
- Port: 5501 (configured in `.vscode/settings.json`)
- Open browser to `http://localhost:5501` to view the live site

### File Structure

```
/
├── index.html                 # Main single-page application
├── css/                       # Stylesheets
│   ├── templatemo-dream-pulse.css  # Custom theme styles
│   ├── bootstrap.min.css      # Bootstrap 4 framework
│   ├── magnific-popup.css     # Lightbox CSS
│   └── all.min.css            # FontAwesome icons
├── js/                        # JavaScript libraries and scripts
│   ├── templatemo-scripts.js  # Custom initialization and event handlers
│   ├── jquery.min.js          # jQuery library
│   ├── parallax.min.js        # Parallax scrolling
│   ├── jquery.magnific-popup.min.js  # Lightbox plugin
│   ├── jquery.singlePageNav.min.js  # Single-page navigation
│   └── slick/                 # Carousel plugin (CSS + JS)
├── img/                       # Images and gallery assets
├── webfonts/                  # FontAwesome font files
├── .htaccess                  # Apache server routing
├── sitemap.xml                # SEO sitemap
└── docs/superpowers/specs/    # Design and planning docs
```

### Dependencies

**Frontend Libraries (bundled, no npm):**
- **Bootstrap 4** — Grid layout and components
- **jQuery** — DOM manipulation
- **Slick** — Carousel/slider functionality
- **Parallax** — Scroll parallax effect
- **Magnific Popup** — Lightbox/modal gallery
- **FontAwesome 5** — Icon library

No package manager is used; all libraries are included as minified files. No build process or transpilation.

---

## Key Sections & Architecture

### Single-Page Structure

The page is organized as a vertical scroll with `id`-based anchors. The sidebar navigation (`#tmSidebar`) links to section IDs, and jQuery Single Page Nav handles active states.

**Main Sections (in order):**

1. **Intro** (`#intro`) — Phone CTA and company tagline
2. **About** (`#about`) — Two-column layout with company info and services
3. **Work** (`#work`) — Gallery of engineering projects (2 galleries: main and civil improvements)
4. **Clients** (`#clients`) — Team achievements, working hours table, MIT affiliation
5. **Talk** (`#talk`) — Contact information and Formspree contact form

### HTML Structure Notes

- **Sidebar Navigation** (`#tmSidebar`) — Fixed left sidebar with navigation, social links, and footer
- **Main Content** (`<main>`) — Scrollable content area with parallax hero
- **Gallery Items** — Use `effect-bubba` class (CSS3 effects) with Magnific Popup for lightbox
- **Contact Form** — Posts to Formspree service (no server-side PHP mail handling)

### Key CSS Classes

- `tm-section` — Main content section wrapper
- `tm-section-wrap` — Section background container
- `tm-color-primary` — Primary accent color
- `tm-gallery` — Gallery grid (Slick carousel)
- `effect-bubba` — CSS3 hover effect on gallery items
- `tm-section-title` — Section heading style
- `.parallax-window` — Parallax scroll container

---

## Contact Form

**Current Implementation:** Formspree integration

```html
<form id="my-form" action="https://formspree.io/f/manajdvn" method="POST">
```

- Form submits via JavaScript fetch (not traditional POST)
- Form fields: phone, name, email, message
- Success message: "Thanks for your submission!"
- No backend processing; Formspree handles email delivery

**Deprecated:** `mail_handler.php` exists but is not used in the active form.

---

## SEO & Metadata

### Current SEO Elements

- **Meta Tags** (in `<head>`):
  - `description` — Company description with location
  - `keywords` — Engineering service keywords
  - `author` — Russell S. Johnson P.E.
  - `viewport` — Mobile responsive viewport
  - `charset` — UTF-8 encoding

- **Sitemap** (`sitemap.xml`) — Currently lists only homepage
- **Alt Text** — Gallery images have descriptive alt attributes
- **Heading Structure** — H1 in sidebar brand, H2s for section titles, H3s for subsections

### SEO Optimization Spec

See `docs/superpowers/specs/2026-05-20-seo-optimization-design.md` for planned SEO improvements:
- On-page optimization (keyword targeting, meta tags, heading hierarchy)
- Structured data (LocalBusiness, ProfessionalService schemas)
- Technical SEO fixes (mobile optimization, Core Web Vitals)
- Local SEO (geo-targeting, Google Business Profile)

---

## Common Tasks

### Adding/Modifying Content

1. **Edit Section Text** — Find the section in `index.html` (e.g., `#about`) and update the text directly
2. **Add Gallery Images** — Place image in `img/gallery/` folder, then add a new `.tm-gallery-item` block to the corresponding gallery section
3. **Update Contact Info** — Edit phone numbers in both the intro section and "Talk to Us" address block
4. **Modify Section Layout** — Use Bootstrap grid classes (`.row`, `.col-*`) for responsive layout changes

### Updating Styles

- **Global Styles** — Edit `css/templatemo-dream-pulse.css`
- **Inline Styles** — Some custom styles are in `<style>` tag in HTML head (move to CSS file if expanding)
- **Theme Colors** — Defined in `templatemo-dream-pulse.css` (search for `.tm-color-primary`)

### Testing Changes Locally

1. Start Live Server (`F5` or right-click → "Open with Live Server")
2. Browser auto-refreshes on file save
3. Test responsive design: DevTools → Toggle device toolbar (Ctrl+Shift+M)
4. Test cross-browser: Check in Firefox, Chrome, Safari

### Deploying Changes

The site is hosted on a static web server (Apache, based on `.htaccess`). Deployment typically involves:
1. Committing changes to git
2. Pushing to the hosting provider (likely via git or FTP)
3. Verifying changes on the live domain

---

## Git Workflow

**Branch:** `main` (single branch for this simple site)

**Commit Convention:**
- Use descriptive messages (e.g., "Add MIT logo to clients section")
- Prefix with type: `Design:`, `Fix:`, `Content:`, `Style:` (see recent commits)

**Recent Work:**
- Design: SEO optimization for single-page site (2026-05-20)
- Async form improvements
- Image optimization

---

## Notes for Future Work

- **No build system** — Future enhancements should maintain this simplicity; avoid adding Webpack, Gulp, etc. unless essential
- **Single page only** — All SEO and content work is constrained to `index.html`
- **Library versions** — jQuery, Bootstrap, etc. are minified and bundled; updating requires manual replacement
- **Contact form** — Uses Formspree (external service); no server-side form processing
- **Performance** — Parallax and carousels add overhead; test Core Web Vitals when making visual changes
- **Accessibility** — Site has good ARIA labels and semantic HTML; maintain this in edits

---

## Useful Links

- **Domain:** https://civilstructuralengineers.com
- **Formspree Form:** https://formspree.io/f/manajdvn
- **Google Business Profile:** https://civil-structural-engineering-company-pllc.business.site
- **Facebook:** https://www.facebook.com/Civil-Structural-Engineering-Company-PLLC-101595881907173
- **Template Source:** TemplatesMo Dream Pulse template (no longer actively used as boilerplate)

