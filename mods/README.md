# Mods

A **mod** is a panel, not a whole window: a small program Herdr draws in a block of a layout, in a
pane of its own, or as an overlay. Layouts live in [`../layouts/`](../layouts/).

Each folder here is one mod package, shaped like `~/.config/herdr-app` so it can be copied in
whole:

```
mods/<mod>/
  mods/<mod>/        main.js (required), mod.json (where it first appears), its svg/images/fonts
  RECIPE.md          the brief: what you see, how it behaves, how it is built
  preview.png        a screenshot of the real thing
  keys.json          optional: the keys it expects, merged into the person's keys.json
```

Nothing is here yet. To add one:

1. Write or clone the mod into `mods/<mod>/mods/<mod>/`, with the `RECIPE.md` and `preview.png`
   beside it (see any shipped mod in `~/.config/herdr-app/mods/` for what a mod looks like).
2. `herdr-app check mods/<mod>/mods/<mod>` — a mod is never done without a passing check.
3. Put it in the person's home and in a layout:

   ```sh
   cp -R mods/<mod>/mods/<mod> ~/.config/herdr-app/mods/
   ```

   Either `mod.json`'s `"place"` docks it on first sight, or a layout names it — a block
   `{"type": "block", "content": {"mod": "<mod>"}}`, or a pane split with `mod` in its props.

The `.d.ts` and `jsconfig.json` files Herdr generates inside a mod folder are gitignored: they are
not source, and they come back on the next start.
