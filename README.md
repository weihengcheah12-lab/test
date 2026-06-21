# Galaxy Conquest — deployable site

This folder is the **entire hostable game**. Two files, nothing to build:

- `galaxy-conquest.html` — the whole game (self-contained: HTML + CSS + JS in one file).
- `index.html` — entry point; redirects the bare URL to `galaxy-conquest.html`.

There is no build step and no bundler. The only thing fetched at runtime is **PeerJS**
(from a CDN), and only when you start an **online** game — single-player vs AI and local
hotseat work fully offline / over `file://`.

## Host on GitHub Pages
1. Commit this repo to GitHub.
2. **Settings → Pages → Build and deployment → Deploy from a branch.**
3. Branch: your default branch · Folder: **`/docs`** · Save.
4. Your game is live at `https://<user>.github.io/<repo>/` (the `index.html` forwards to the game).

## Or host anywhere else
Any static host works (Netlify, Cloudflare Pages, an S3 bucket, `python -m http.server`,
or just open `galaxy-conquest.html` directly). No server-side code is required.

## Online multiplayer note
Online play is peer-to-peer over WebRTC using the free public PeerJS broker for signaling
(no server of your own). On restrictive/symmetric-NAT networks the direct connection can
fail without a TURN relay (none is configured) — it works on most home networks.
