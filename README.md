# POKO

A sticky notes board that runs in the browser. Notes, images and arrows sit on a free canvas,
you can keep several boards, and everything stays on your own computer. It works offline and can
be installed as an app.

POKO is the rebuilt version of NOTEPOKO, an earlier sticky notes app.

## What it does

- Multiple boards, each with notes, images and arrows between them.
- Undo on each board.
- Saves automatically to the browser's own storage. Nothing is uploaded.
- Export all boards to a file and import them again, including boards from the older NOTEPOKO.
- Installs as an app and works offline when served over http.

## How it is built

The whole app is one file, `index.html`, with plain HTML, CSS and JavaScript and no framework or
build step.

- The app keeps its state in plain objects and builds the page from them. Inputs write straight
  back into that state, so the page is never the source of truth.
- Boards, images and settings are stored in IndexedDB. Images are stored once as Blobs and notes
  refer to them by id.
- If the tab closes with unsaved changes, those boards are copied to localStorage and picked up
  the next time POKO opens.
- `sw.js` and `manifest.webmanifest` make it installable and usable offline.

## Running it

Open `index.html` in a browser to use it straight away.

To install it as an app and use it offline, serve it over http:

```
node serve.js
```

Then open http://localhost:5174.

Opening the file directly and opening it through the server keep separate storage, so use
Export all and Import to move boards between them.
