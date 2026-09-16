# Colouring Book 🎨🖌️

A single-screen Android app, built with **MIT App Inventor**, that turns outline images into a digital colouring book — pick a colour, adjust brush size, and draw with your finger.

## How it works

1. The app loads the first outline image onto the canvas automatically
2. Tap a colour swatch (e.g. **RED**, **BLUE**, **YELLOW**) to set your paint colour
3. Drag the slider to adjust line thickness
4. Draw directly on the image by dragging your finger across the canvas
5. Tap **NEXT** / **BACK** to move to a different outline image
6. Tap **CLEAR** to wipe the canvas and start over

## Features

- 🎨 7-colour palette — Grey, Green, Red, Yellow, Orange, Pink, Blue
- ✏️ Freehand drawing via `Canvas.DrawLine` on drag
- 🎚️ Adjustable brush/line width via a slider
- 🧹 One-tap **CLEAR** to reset the canvas
- ⏭️⏮️ **NEXT** / **BACK** buttons to cycle through multiple outline images
- 🖥️ Simple single-screen UI — no typing needed

## Tech Stack

- **Platform:** MIT App Inventor (block-based, no native code)
- **Components:** `Canvas1`, `Slider1`, colour `Button`s (GREY, GREEN, RED, YELLOW, ORANGE, PINK, BLUE), `CLEAR`, `NEXT`, `BACK` buttons
- **Variables:** `global IMAGENUMBER` — tracks which outline image is currently loaded
- **Media:** numbered `.jpeg` outline images (`1.jpeg`, `2.jpeg`, …)

## How the Blocks Work

| Event | Action |
|---|---|
| `Screen1.Initialize` | Loads the first image (`join(IMAGENUMBER, ".jpeg")`) as `Canvas1.BackgroundImage` |
| Colour button `.Click` | Sets `Canvas1.PaintColor` to that colour |
| `Slider1.PositionChanged` | Sets `Canvas1.LineWidth` to `thumbPosition` |
| `Canvas1.Dragged` | Calls `Canvas1.DrawLine` from the previous touch point to the current one |
| `CLEAR.Click` | Calls `Canvas1.Clear` |
| `NEXT.Click` | If not on the last image, increments `IMAGENUMBER` and updates the background |
| `BACK.Click` | If not on the first image, decrements `IMAGENUMBER` and updates the background |

## Example

| Action        | Result                          |
|---------------|----------------------------------|
| Tap RED       | Paint colour set to red          |
| Drag slider   | Line width increases/decreases   |
| Draw on canvas| Coloured line follows your finger|
| Tap NEXT      | Loads the next outline image     |
| Tap CLEAR     | Canvas wiped blank                |

## Screenshot

![App Screenshot](screenshot.png)

*The app in action — colouring an outline image with the palette and slider.*

## Limitations (v1.0)

- Only supports drawing with a single line width at a time (no per-stroke variation)
- No eraser tool
- No save/export of finished artwork
- Fixed colour palette — no custom colour picker
- Requires images to be pre-loaded as numbered media assets

## Future Improvements

- Add an eraser tool
- Add a custom colour picker (not just fixed swatches)
- Add save/export functionality for finished drawings
- Add more outline images / categories
- Add undo/redo for strokes

---
*Built as a mini project — MIT App Inventor, block-based development.*
