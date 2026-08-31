# Prompt Loom

A notebook-style UI for writing production system prompts — not a chat playground. Prompts here are things you keep, reread, and version, not things you fire off and forget.

## Running it

Open `promptloom.html` directly in a browser. No build step, no install, no dependencies.

```powershell
code "promptloom.html"
```

## What's here

- **Library rail** — a list of saved prompts, each with a title and a version tag (`v1`, `v2`, `draft`, etc.). Filter it with the search field, add a new entry with "New prompt."
- **Per-entry actions** — duplicate (copies the entry after the original) and delete (removes it immediately but shows a 6-second "Undo" toast before it's gone for good).
- **The writing page** — a ruled sheet sized and spaced for long-form system prompts, not short chat messages. Grows as you type, up to a point, then scrolls internally rather than stretching the whole page.
- **Word and token counts** — the token figure is a rough estimate (`characters ÷ 4`), useful for a sense of budget, not exact.
- **Autosave** — every edit saves to `localStorage` about 600ms after you stop typing. The line under the title tells you what's happening ("Saving…" / "Saved just now") instead of saving silently.
- **Export / Import** — Export downloads every entry as one JSON file. Import reads a file back in and adds those entries alongside what's already there (new IDs, so it never overwrites). This doubles as your backup path.
- **Multi-tab awareness** — if the notebook changes in another tab, a banner offers to reload rather than silently clobbering what's open.
- **Keyboard access** — the entry list is a proper `listbox`; arrow keys move between entries, Enter/Space selects.

## Known limitations (this is a prototype, not an MVP)

- **Storage is local and single-device.** `localStorage` doesn't sync across browsers or machines, and clearing site data wipes it. Export regularly if you care about what's in here.
- **Version tags aren't real versions.** `v1`/`v2`/`v3` are just labels you type — editing an entry overwrites it in place. There's no snapshot history behind the tag yet.
- **No accounts, no sharing, no backend.** Everything runs in one browser tab's storage.
- **Multi-tab conflicts aren't merged**, just flagged. Reloading takes whichever version is in storage; anything unsaved in the other tab is lost.

## Customizing

- Color tokens are the CSS variables at the top of the `<style>` block (`--accent`, `--bg`, `--ink`, etc.) — all one soft-blue family by design.
- Type is Newsreader (serif, for the wordmark and entry titles) paired with Inter (everything functional), loaded from Google Fonts.
- Everything — markup, styles, and JS — lives in the single `promptloom.html` file.
                      
