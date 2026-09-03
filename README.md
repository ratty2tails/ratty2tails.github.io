# ratty2tails.github.io

Source for The Ratty2Tails Papers archive site — a free, static home for
the Monetary History and Machine Series essays, built to sit alongside
the existing PDF pipeline rather than replace it.

## How it's laid out

```
index.html                  Homepage — both series, ledger-row style
monetary-history/index.html Full Monetary History listing
machine-series/index.html   Full Machine Series listing
essays/                     One HTML page per essay, plus _template.html
pdfs/                       Drop the matching PDF for each essay here
assets/                     cover-placeholder.svg — swap for the real portrait
css/style.css               Shared stylesheet (the whole design system)
```

Every essay page already exists under `essays/`, filled in with the
title, one-line description, and correct series breadcrumb pulled from
what's already been published — the body content is placeholder text
ready to be replaced with the real essay.

## Publishing it (one-time setup)

1. Create a GitHub repo named exactly `ratty2tails.github.io` (the name
   matters — GitHub serves user/org sites from a repo with this exact
   name).
2. Push everything in this folder to the `main` branch, at the repo
   root.
3. In the repo's **Settings → Pages**, set the source to "Deploy from
   branch", branch `main`, folder `/ (root)`. Save.
4. It'll be live at `https://ratty2tails.github.io` within a minute or
   two — no build step, no server, no cost.

```
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<your-username>/ratty2tails.github.io.git
git push -u origin main
```

## Adding a new essay

1. Copy `essays/_template.html` to `essays/your-essay-slug.html`.
2. Fill in the title, series label, byline date, TL;DR, and body
   sections. Reuse `<span class="dropcap">` and any hand-authored SVG
   diagrams straight from the PDF source — the markup is compatible.
3. Drop the rendered PDF into `pdfs/your-essay-slug.pdf`.
4. Add a matching ledger row (copy an existing `<article class="entry">`
   block) to the homepage and to the relevant series index page.

## Swapping in the real cover portrait

Replace `assets/cover-placeholder.svg` with the actual Ratty2Tails
portrait (e.g. `cover.jpg`), then update the one `<img src="...">`
reference in `index.html` to match. The rounded-rectangle frame is
already styled in `css/style.css` under `.masthead-portrait`.

## Optional: a custom domain

The site works as-is at `ratty2tails.github.io`. To point a subdomain
of videoteq.co.uk or peggybot.xyz at it instead: add a `CNAME` file at
the repo root containing just the domain, then add a matching DNS
record (CNAME to `<your-username>.github.io`, or an ALIAS/ANAME record
if pointing the bare domain) with whichever registrar or DNS host
those domains use. GitHub's own docs walk through this under
"Managing a custom domain for your GitHub Pages site."

## Design notes

The visual language is a ledger book, not a blog template: hairline
rules instead of cards, entries read left-to-right like a ledger line
(title, then Read/PDF marks aligned right like a ledger's amount
column), and the one accent colour — an antique brass/gold — is
reserved for hovers and the PDF mark rather than spread across the
page. Typefaces (Fraunces, Source Serif 4, Archivo) echo the ones
already used in the PDF pipeline for continuity between the two
formats.
