# Migration KPI Dashboard — Vercel deploy

Static site. One file: `public/index.html`. No build step, no dependencies.

## Option A — Vercel CLI (fastest)

```bash
cd migration-dashboard
npx vercel login          # opens your browser
npx vercel --prod
```

Accept the defaults when prompted:

- Set up and deploy? **Y**
- Which scope? *your account or team*
- Link to existing project? **N**
- Project name? `migration-kpi-dashboard`
- In which directory is your code located? `./`
- Want to modify build settings? **N**

You get a `https://<project>.vercel.app` URL. Re-run `npx vercel --prod` after any edit.

## Option B — Git import

1. `git init && git add -A && git commit -m "migration kpi dashboard"`
2. Push to a GitHub/GitLab/Bitbucket repo.
3. vercel.com → **Add New → Project** → import the repo → **Deploy**.
   Framework preset: **Other**. Build command: *(leave empty)*. Output directory: `public`.

Every push to the default branch redeploys.

## Before you share the URL

This page contains internal record counts and storage volumes for your
production Zoho Projects data. A Vercel deployment is **public by default** —
anyone with the URL can read it.

In the Vercel dashboard: **Project → Settings → Deployment Protection**, turn on
**Vercel Authentication** so only members of your Vercel team can open it.
Check that it covers *production* and not just preview deployments — on some
plans production protection needs a paid tier. Verify in a private window before
sending the link to anyone.

`vercel.json` already sets `X-Robots-Tag: noindex, nofollow` so search engines
skip it, but that is not access control.
