# PMB Engineering — website

Static one-page site for PMB Engineering (Paul Boucher). Plain HTML, no build step.

## Files
- `index.html` — the whole site (self-contained; only external calls are Google Fonts)
- `favicon.svg` — handwritten "PMB" tab icon
- `.nojekyll` — tells GitHub Pages to serve files as-is

## Deploy to GitHub Pages — web UI (2 minutes, no command line)
1. On GitHub: **New repository**. Name it `pmb-engineering` (or, to serve at `USERNAME.github.io`, name it exactly `USERNAME.github.io`). Set **Public**.
2. On the new repo page: **Add file -> Upload files**. Drag in `index.html`, `favicon.svg`, and `.nojekyll`. **Commit**.
3. **Settings -> Pages**. Under *Build and deployment*, Source = **Deploy from a branch**, Branch = **main**, folder = **/ (root)**. **Save**.
4. Wait ~1 min. Your site is at `https://USERNAME.github.io/pmb-engineering/` (or `https://USERNAME.github.io/` if you used the special repo name).

## Deploy with the gh CLI (if you prefer)
```bash
cd pmb
git init && git add . && git commit -m "PMB Engineering site"
gh repo create pmb-engineering --public --source=. --push
gh api -X POST repos/:owner/pmb-engineering/pages -f "source[branch]=main" -f "source[path]=/"
```

## Custom domain (pmb-engineering.com) — optional
1. Add a file named `CNAME` (no extension) containing one line: `pmb-engineering.com`
2. At your DNS registrar, add these A records for the apex domain:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   and a `CNAME` for `www` -> `USERNAME.github.io`.
3. Settings -> Pages -> Custom domain -> enter `pmb-engineering.com`, enable **Enforce HTTPS**.

DNS can take up to a few hours to propagate.
