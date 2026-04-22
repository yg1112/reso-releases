# reso-releases

Official releases and downloads for **Reso Notes** — the macOS voice transcription app served at [reso.dzgapp.com](https://reso.dzgapp.com).

## Scope — do NOT cross the streams

This repo is **Reso Notes only** (source: [yg1112/reso](https://github.com/yg1112/reso), bundle id `com.dzgapp.reso.direct`). It is the single source of truth for direct-channel DMGs that `reso.dzgapp.com` downloads and Sparkle OTA clients auto-update from.

**The successor app** — Reso Nebula / "Reso2" (source: [yg1112/Reso2](https://github.com/yg1112/Reso2), bundle id `com.dzg.Reso2`) — publishes to a **separate** public release repo: [yg1112/reso2-releases](https://github.com/yg1112/reso2-releases), which powers [resoapp.xyz](https://resoapp.xyz).

```
yg1112/reso    → yg1112/reso-releases    → reso.dzgapp.com   (Reso Notes)
yg1112/Reso2   → yg1112/reso2-releases   → resoapp.xyz       (Reso Nebula)
```

### Do NOT publish Reso Nebula / Reso2 artifacts here

Between 2026-04-14 and 2026-04-15 two Reso Nebula releases (v1.2.0, v1.2.1) were published here by mistake before the two products' pipelines were split. They were cleaned up on 2026-04-22 and the split is now canonical (see commit [`1da3d23`](https://github.com/yg1112/reso/commit/1da3d23) on yg1112/reso). Publishing Reso Nebula DMGs here again would:

- Silently break `reso.dzgapp.com`'s Download button for direct-channel users (GitHub `/releases/latest` may pick the wrong binary).
- Push Sparkle clients onto the Reso Nebula binary on next auto-update — they run under a different bundle id (`com.dzg.Reso2`), so the app would effectively uninstall itself for existing users.

### If you're preparing a release

- **Reso Notes**: run [`scripts/deploy.sh`](https://github.com/yg1112/reso/blob/master/scripts/deploy.sh) in the [`yg1112/reso`](https://github.com/yg1112/reso) repo. It handles DMG build, upload to this repo, appcast bump, and CF Pages redeploy.
- **Reso Nebula**: see [`yg1112/Reso2`](https://github.com/yg1112/Reso2)'s own release flow. **Never** upload its DMGs here.

## Downloads

Latest: <https://github.com/yg1112/reso-releases/releases/latest/download/Reso.dmg>

Sparkle feed: <https://reso.dzgapp.com/appcast.xml>