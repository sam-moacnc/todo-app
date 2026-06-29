# Todo App

A minimal, single-file todo list that runs entirely in the browser. No build step, dependencies, or backend required.

## Features

- **Add tasks** — Type a task and submit the form (or press Enter).
- **Mark complete** — Toggle the checkbox to strike through finished tasks.
- **Delete tasks** — Click the × button to remove a task.
- **Persistent storage** — Tasks are saved in `localStorage` under the key `todos` and restored on reload.
- **Empty state** — Shows “No tasks yet.” when the list is empty.

## Quick start

Open `index.html` in any modern browser:

```bash
# From the project root
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

Or serve the folder locally:

```bash
python3 -m http.server 8000
# Then visit http://localhost:8000
```

## Project structure

```
todo-app/
└── index.html   # HTML, CSS, and JavaScript in one file
```

## How it works

### Data model

Each todo is stored as a JSON object:

```json
{ "text": "Buy groceries", "done": false }
```

The full list is serialized to `localStorage` whenever tasks are added, toggled, or deleted.

### UI

| Element | ID | Purpose |
|---------|-----|---------|
| Form | `#form` | Submit new tasks |
| Input | `#input` | Task text (placeholder: “Add a task…”) |
| List | `#list` | Renders todo items |
| Empty message | `#empty` | Hidden when at least one task exists |

Each list item contains a checkbox, task label, and delete button.

### Core functions

- **`save()`** — Writes `todos` to `localStorage` and re-renders the list.
- **`render()`** — Rebuilds the DOM from the in-memory `todos` array.
- **Form submit handler** — Trims input, ignores empty strings, appends `{ text, done: false }`, clears the input, then saves.

## Tech stack

- Plain HTML5, CSS3, and vanilla JavaScript
- Browser `localStorage` API
- System UI font stack, responsive layout (max-width 360px)

## Browser support

Works in any browser that supports ES5+ JavaScript and `localStorage` (all modern browsers).
