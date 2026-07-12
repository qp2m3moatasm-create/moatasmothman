# Motasm Othman — Personal Website

Personal portfolio site for Motasm Othman (معتصم العثمان) — photographer, graphic
designer, and video editor. Plain HTML/CSS/JavaScript, no build step, no
framework, no backend — 100% static and ready for GitHub Pages.

## Project structure

```
.
├── index.html              ← entry point, open this directly to preview locally
├── favicon.svg / favicon.ico / apple-touch-icon.png / icon-192.png / icon-512.png
├── site.webmanifest        ← PWA manifest
├── robots.txt
├── sitemap.xml
└── assets/
    ├── css/style.css       ← all styles (dark/light themes, animations, responsive)
    ├── js/script.js        ← all behavior (i18n AR/EN, theme toggle, reveal
    │                          animations, particles, QR code, etc.)
    └── images/             ← profile photos (JPG + WebP)
```

Every asset is referenced with a **relative path** (`./assets/...`), so the
site works correctly whether it's hosted at the root of a domain
(`https://your-username.github.io/`) or inside a project subpath
(`https://your-username.github.io/your-repo/`) — no configuration needed.

## How to publish on GitHub Pages

### Option A — User/organization site or a dedicated repo (recommended)

1. Create a new GitHub repository (e.g. `motasm-othman-website`).
2. Upload **the entire contents of this `github-pages` folder** to the root
   of that repository (not the folder itself — its *contents*: `index.html`,
   `assets/`, `favicon.svg`, etc. should sit directly at the repo root).
   - Using the GitHub web UI: click "Add file" → "Upload files" and drag in
     everything inside this folder.
   - Using Git:
     ```bash
     cd github-pages
     git init
     git add .
     git commit -m "Initial commit"
     git branch -M main
     git remote add origin https://github.com/<your-username>/<your-repo>.git
     git push -u origin main
     ```
3. In the repository, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch".
5. Choose branch `main` and folder `/ (root)`, then click **Save**.
6. Wait 1–2 minutes. Your site will be live at:
   - `https://<your-username>.github.io/<your-repo>/` (project site), or
   - `https://<your-username>.github.io/` (if the repo is named
     `<your-username>.github.io`, a special "user site" repo).

### Option B — Publish from a `/docs` folder on an existing repo

1. Copy the contents of this `github-pages` folder into a `docs/` folder at
   the root of your existing repository.
2. Commit and push.
3. In **Settings → Pages**, set the source to branch `main` (or your default
   branch) and folder `/docs`.

## After publishing — two small things to personalize

Once you know your final published URL, open these two files and replace
the placeholder URL with the real one (they don't block the site from
working, they only help search engines):

- `sitemap.xml` — update the `<loc>` value.
- `robots.txt` — optionally switch the `Sitemap:` line to the full absolute
  URL instead of the relative one.

## Local preview

Because the site uses `fetch`-free, plain relative paths, you can just open
`index.html` directly in a browser for a quick look. For a fully accurate
preview (some browsers restrict things like the Web Share API or service
workers on `file://`), serve it locally instead:

```bash
# Node (no install needed, Node 18+)
npx serve .

# or Python
python3 -m http.server 8080
```

Then visit `http://localhost:8080` (or whatever port is shown).

## Features

- Bilingual: Arabic (default, RTL) / English, toggled at runtime.
- Dark/light theme toggle (persisted).
- Scroll-reveal animations, animated hero profile photo, particle
  background, typewriter role rotator.
- QR code (loaded lazily from a CDN) linking to the live site.
- Fully responsive, from small phones to large desktops.
- Client-side "not found" view for any unexpected deep link.

## Notes

- Google Fonts (Cairo, Inter) are loaded from Google's CDN — no self-hosted
  font files needed, and no build step required.
- The QR code library (`qrious`) is loaded lazily from a CDN with a
  graceful text-link fallback if it fails to load — no bundler needed.
- No backend, database, or API calls are required anywhere on this site.
