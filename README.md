# Kotoba — Japanese Learning Website

A mobile-first Japanese learning website designed for GitHub Pages.

## What this project does

- 13,000+ kanji support through KANJIDIC2-derived data
- 20,000+ common vocabulary support through JMdict-derived data
- JLPT N5–N1 filtering when level data is present
- Kanji search by character, meaning and reading
- Vocabulary search
- Radicals/components
- Curated Japanese-English example sentences
- Grammar browser
- KanjiVG stroke-order SVG display
- Writing canvas for finger practice
- Japanese speech using the browser's built-in speech synthesis
- Local spaced-repetition progress
- Streaks, mastered cards and reviews
- Favorites
- Dark mode
- Import/export progress
- No server, login or paid API required

## Folder structure

```text
kotoba/
├── index.html
├── style.css
├── app.js
├── data-loader.js
└── README.md
```

## Put it on GitHub Pages

1. Create a new GitHub repository.
2. Upload the five files above.
3. Make sure `index.html`, `style.css`, `app.js` and `data-loader.js` are in the repository root.
4. Open **Settings → Pages**.
5. Select **Deploy from a branch**.
6. Select `main` and `/ (root)`.
7. Save.
8. Open the GitHub Pages URL after deployment.

The app fetches its large JSON datasets directly from the configured open-data repository, so you do NOT need to paste tens of thousands of records into `index.html`.

## Important: data source and licensing

The default loader points to:

https://github.com/jkindrix/japanese-language-data

That project currently describes its committed core dataset as:

- `data/core/kanji.json` — 13,108 KANJIDIC2-derived kanji
- `data/core/words.json` — 23,119 common vocabulary entries
- `data/core/radicals.json` — 253 radicals
- `data/corpus/sentences.json` — 25,980 curated JA–EN sentence pairs
- `data/grammar/grammar.json` — 595 grammar points
- `data/enrichment/stroke-order-index.json` — stroke-order lookup
- `data/enrichment/stroke-order/*.svg` — KanjiVG stroke graphics

The combined dataset is published under CC-BY-SA 4.0 according to that repository's current README/manifest. KanjiVG itself is CC-BY-SA 3.0.

Read the upstream attribution/license files before distributing a public copy of the data.

## Monthly data updates

The upstream project's README states that its EDRDG-derived data has a monthly update obligation for web-facing dictionary applications.

Because Kotoba loads the upstream data at runtime, keep the data source current and retain the required attribution.

## If you want to host your own data

Fork or copy the permitted data into your own repository and change `DATA_BASE` in `data-loader.js`:

```js
const DATA_BASE =
  "https://raw.githubusercontent.com/YOUR-USERNAME/YOUR-REPO/main/data";
```

Then keep the same folder structure expected by `data-loader.js`.

## Notes

### GitHub Pages and ES modules

Kotoba uses:

```html
<script type="module">
```

GitHub Pages serves HTTPS, so this works on the deployed site.

Do not test the site by opening `index.html` directly as a `file://` URL if your browser blocks module/data requests. Use GitHub Pages or another local web server.

### Stroke order

KanjiVG does not cover every one of the 13,108 KANJIDIC2 characters. The upstream project reports complete KanjiVG coverage for the 2,136 Jōyō kanji and partial coverage for rarer characters. Kotoba therefore shows a friendly fallback when an SVG is unavailable.

### Grammar

The upstream project's current grammar data is described as draft and not native-speaker reviewed. Treat it as study material, not an authoritative grammar reference.

## Attribution

Kotoba is an independent UI/application. It is not affiliated with Moji or the Japanese-language-data maintainers.

Credit the upstream projects when distributing the data:

- JMdict / EDRDG
- KANJIDIC2 contributors
- KanjiVG / Ulrich Apel and contributors
- Tatoeba contributors
- Waller JLPT lists
- Kanjium contributors
- Wikipedia/Kangxi radical sources
- jmdict-simplified
- japanese-language-data maintainers

See the upstream project's `ATTRIBUTION.md` and `LICENSE` for exact wording and obligations.

## Roadmap

Possible future additions:

- Kana lessons
- True animated stroke-order tracing
- Better SRS scheduling
- Daily goals
- Vocabulary decks
- Pitch-accent visualization
- Grammar quizzes
- Offline PWA
- Install button
- Backup/sync
- More learning statistics
