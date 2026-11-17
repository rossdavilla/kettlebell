# KB Builder (`kettlebell`)

Ross's personal kettlebell workout builder: pick equipment, level and categories, generate a
workout, then track rounds. Live at <https://rossdavilla.github.io/kettlebell/>.

`README.md` has the file-by-file map — read it first. The notes here are what it does not say.

## How it is put together

| Path | Role |
|---|---|
| `index.html` | builds the workout and tracks rounds |
| `library.html` | the movement library; deep-link a move with `library.html#<move-slug>` |
| `js/exercises.js` | **the data layer** — all 82 moves, their curated demo videos, and the workout generator |
| `js/app.js`, `js/library.js` | per-page logic |
| `css/styles.css` | shared styles |
| `images/moves/<move-slug>.png` | optional 3:2 start/end diagram for a move |

Plain static site: no build step, no framework, no package manager. State lives in
`localStorage` on the phone; there is no backend.

## Conventions worth keeping

- **`js/exercises.js` is the single source of truth for moves.** Adding or editing a move means
  editing that file, not the pages. The slug is the identity: it keys the library anchor, the
  diagram file name, and the generator.
- **Diagrams are optional and slug-named.** When `images/moves/<move-slug>.png` exists the card
  shows it instead of the video thumbnail; moves without one keep the thumbnail. Do not make a
  diagram required.
- Each move's library entry carries setup, steps and common mistakes. Match the voice of the
  entries already there.
- The exercise data and generator logic are adapted from
  [Kettlebell Flow](https://gustlv1.github.io/kettlebell-flow/) — keep that credit in the README.

It is used from a phone in a garage, so check phone width and keep controls thumb-sized.

## Publishing

GitHub Pages serves `main` from the repository root, so a push to `main` is the deploy. Already
listed in `data/sites.json` in the
[`rossdavilla.github.io`](https://github.com/rossdavilla/rossdavilla.github.io) repo under the
`personal` tag.
