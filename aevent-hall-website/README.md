# A.Event Hall — website files

This folder is the whole website: `index.html` plus an `images/` folder it references. No build step, no dependencies — it's ready to publish as-is.

## What's in here

```
index.html            the site (bilingual EN/中文, one page)
images/
  logo-mark.png
  runway-black-gown.jpg
  favicon-16.png, favicon-32.png, favicon-192.png, favicon-512.png, apple-touch-icon.png
  clients/             11 past-event photos
  setups/              4 space-layout photos
```

## Deploy with GitHub Pages (free, ~5 minutes)

1. **Create a repository.** On [github.com](https://github.com), click **New repository**. Name it anything (e.g. `aevent-hall-site`). Keep it **Public** — GitHub Pages' free tier requires a public repo. Don't add a README, .gitignore, or license — you already have these files.

2. **Upload the files.** On the new repo's page, click **uploading an existing file**, then drag in `index.html` and the whole `images` folder (drag the folder itself — GitHub preserves the structure). Commit directly to `main`.

   *(If you'd rather use git from your computer instead of the browser uploader — see "Using git from the command line" below.)*

3. **Turn on Pages.** In the repo, go to **Settings → Pages** (left sidebar, under "Code and automation"). Under **Build and deployment → Source**, choose **Deploy from a branch**. Under **Branch**, choose `main` and folder `/ (root)`, then **Save**.

4. **Wait ~1 minute, then find your link.** Refresh the Pages settings page — it'll show a green box with your live URL, something like:
   `https://your-username.github.io/aevent-hall-site/`

That's it — the site is live. Any time you push a change to `main`, it redeploys automatically in under a minute.

## Before you share the link (2-minute checklist)

A few tags in `index.html` reference a placeholder domain because the real one wasn't known until now. Open `index.html` in any text editor, find these lines near the top (search for `YOUR-DOMAIN-HERE`), and replace the placeholder with your actual GitHub Pages URL (or custom domain, if you set one up):

```html
<link rel="canonical" href="https://YOUR-DOMAIN-HERE/">
<meta property="og:url" content="https://YOUR-DOMAIN-HERE/">
```

This isn't required for the site to work — it only affects how search engines and link-preview cards (WhatsApp, Facebook, etc.) identify the canonical page.

## Using a custom domain instead of the github.io address

If you own a domain (e.g. `aeventhall.com`) and want the site there instead of `github.io`:

1. In **Settings → Pages**, under **Custom domain**, enter your domain and save. GitHub creates a `CNAME` file in your repo automatically.
2. At your domain registrar (wherever you bought the domain), add the DNS records GitHub shows you — usually a `CNAME` record pointing to `your-username.github.io` (for a subdomain like `www.aeventhall.com`) or four `A` records (for the bare root domain `aeventhall.com`). GitHub's Pages settings page shows the exact values to enter.
3. DNS changes can take a few minutes to a few hours to take effect. Once they do, check **Enforce HTTPS** in the same settings panel so visitors always get the secure `https://` version.

## Using git from the command line (optional, instead of step 2 above)

If you're comfortable with git:

```bash
cd path/to/this/folder
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/your-username/aevent-hall-site.git
git push -u origin main
```

Then continue from step 3 above (turning on Pages).

## Making future edits

- **Text changes** (prices, copy, phone number): open `index.html` in any text editor, search for the text you want to change, and edit it directly — it's plain HTML, readable top to bottom by section (Hero, Intro, Spaces, Amenities, Past Events, Rates, Enquire).
- **Swapping a photo**: replace the file in `images/` (keep the same filename) or add a new file and update the matching `src="images/..."` reference in `index.html`.
- **Every English line has a Chinese twin** right next to it (`lang="en"` / `lang="zh"`) — when you change one, update the other so the language toggle stays in sync.
- After editing, commit and push (or re-upload the changed file through the GitHub web interface) — Pages redeploys automatically.

## Notes on what's already handled

- **Mobile-friendly**: tested down to 320px width, no horizontal scrolling, touch targets sized for fingers, images below the fold lazy-load.
- **SEO**: meta description, Open Graph/Twitter preview tags, and structured data (JSON-LD, `EventVenue` schema with your real address and phone) are already in place — see the checklist above for the one placeholder to fill in.
- **Fonts**: loaded from Google Fonts over HTTPS — no local font files to manage.
- **No backend, no database, no build tools** — it's a static site, so GitHub Pages (or literally any static host — Netlify, Vercel, Cloudflare Pages) can serve it without configuration.
