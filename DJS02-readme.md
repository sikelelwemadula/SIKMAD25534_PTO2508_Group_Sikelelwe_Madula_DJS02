# DJS02 - Podcast App

## Project Overview

We were required to build a small podcast discovery app built with native HTML, CSS, and JavaScript. It displays a gallery of podcast preview cards and uses a custom modal interface for viewing more details about each show.

The app is designed to demonstrate component-driven architecture using a native Web Component for the podcast card, while keeping the main app code separate from the UI card implementation.

## Key Features

- Grid layout for browseable podcast cards
- Responsive design for desktop and mobile
- Custom filtering by podcast properties
- Modal detail view triggered from each card
- Encapsulated card UI using a custom HTML element

## Custom HTML Element: `podcast-card`

The core reusable piece of this project is the `podcast-card` custom element defined in `src/components/PodcastCard.js`.

### What it does

- Creates a new element called `<podcast-card>` using `customElements.define("podcast-card", PodcastCard)`
- Uses the Shadow DOM via `this.attachShadow({ mode: "open" })` to isolate styles and markup
- Renders podcast data inside its own template, including:
  - cover image
  - title
  - season count
  - genre tags
  - last updated date

### How it works

- The app passes podcast data into the component using the `setPodcast(podcast)` method.
- The `renderPodcast()` function updates the internal DOM with the podcast details.
- When the card is clicked, the component emits a custom event named `podcast-selected`.
- This event bubbles up through the DOM, allowing the parent application to respond without tightly coupling to the card implementation.

### Why this is useful

Using a custom HTML element makes the podcast card reusable and modular:

- styles are encapsulated and do not leak globally
- the card logic is self-contained
- the main app only needs to supply data and listen for the custom event
- the card can be reused or extended independently from the rest of the page

## Project Structure

- `index.html` — main page markup and component usage
- `styles.css` — global layout and app styling
- `src/index.js` — application entry point and podcast rendering logic
- `src/data.js` — sample podcast data used by the app
- `src/components/PodcastCard.js` — custom web component implementation
- `src/components/createModal.js` — modal behavior and detail view rendering
- `src/utils/DateUtils.js` — date formatting helper
- `src/utils/GenreService.js` — genre lookup and display helper

## How to Run

1. Open `index.html` in a modern browser.
2. Browse the podcast cards.
3. Click a card to open the detail modal.

## Notes

This is a CodeSpace student project and it should be viewed with caution and not replicated without permission.
