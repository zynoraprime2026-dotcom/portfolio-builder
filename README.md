# Portfolio Builder

An artist portfolio web app — build portfolios, add artworks by image URL or AI generation, publish, and share a public gallery link.

## Pages

- **index.html — My Portfolios**: list portfolios with title, artist, artwork count and published status; create new portfolios.
- **portfolio.html — Portfolio Detail**: artwork grid, add artwork (image URL or AI-generated with prompt, size, seed), publish/unpublish toggle, copyable public gallery link.
- **Public Gallery**: served by the Studio API at `/gallery/:id` — a read-only view of a published portfolio, no login needed. Dark teal and cream theme.

## How it works

The app is fully static (no build step). It talks to the Zynora AI Studio API, which provides portfolio storage, AI image generation and the public gallery pages:

- `POST /v1/portfolios` — create
- `GET /v1/portfolios` — list
- `GET /v1/portfolios/{id}` — detail with artworks
- `PATCH /v1/portfolios/{id}` — publish / unpublish / edit
- `POST /v1/portfolios/{id}/artworks` — add artwork (image_url or generate)
- `DELETE /v1/portfolios/{id}/artworks/{aid}` — remove artwork
- `GET /gallery/{id}` — public gallery (no key needed, published only)

Each visitor gets their own free Studio API key automatically on first load (stored in localStorage), so portfolios are private to the browser that created them.

## Deploy

Any static host works (Vercel, Netlify, GitHub Pages). For Vercel: import the repo, framework preset "Other", no build command needed.

## Theme

Dark teal `#0E2A2B` background, cream `#F3ECDA` text, gold `#C9A96A` accents.
