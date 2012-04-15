# deck.automatic.js

An extension for [deck.js][] allowing you to set your presentation to run automatically, with a specified delay between slides.

## Requirements

[deck.js][] ... obviously.

## How does it work

Once the extension is correctly loaded and you've inserted the appropriate control element (see _How to use_), **the presentation will start playing automatically. Clicking on the control element will simply play/pause the presentation.**

## How to use ##

** You can have a look at the example in the repository to check it works, and how it works.**

1. Install by copying the `automatic` folder from the repository to your deck.js `extensions`' folder.

2. Load the extension's `JS` by loading the `.../extensions/automatic/deck.automatic.js` file in your HTML page.

3. You may also want to add the `CSS` (`.../extensions/automatic/deck.automatic.css`), even if I'm pretty sure you'd better come with your own (styling is currently very basic).

4. You **MUST** add a `.deck-automatic-link` element to your `.deck-container` element. The extension currently relies on this element to work. If you don't want to display it, you can just hide it through CSS, this won't prevent it from working.

	For example, you can add: `<div class='deck-automatic-link' title="Play/Pause">Play/Pause</div>` at the end of your `.deck-container` element.
	
## Configuration

The _automatic_ extension follows deck.js' configuration way. It currently declares three options:

1. `startRunning`: can be `true` or `false`. Determines if the presentation start running as soon as it is loaded, or waits for the user to click on the play/pause button.
2. `cycle`: `true` or `false`. If `true`, the presentation goes back to slide 1 when it is running and it comes to the last slide.
3. `slideDuration`: the duration (in milliseconds) during which each slide is displayed.

You can set these options by adding the following code before the `$.deck('.slide')` line:

```
$.extend(true, $.deck.defaults, {

  // other options (core or extensions)

  automatic: {
  	startRunning: false, 	// true or false
  	cycle: false,			// true or false
  	slideDuration: 1000	// duration in milliseconds
  }
}
```

You can also change the classes used for the play/pause element through these options:

```
  classes: {
	automaticRunning: 'deck-automatic-running',
	automaticStopped: 'deck-automatic-stopped'
  },
		
  selectors: {
	automaticLink: '.deck-automatic-link'
  },
```

## TODOs

* **Provide functions on deck to play/pause the presentation ** (such as `$.deck('play')`).
* Remove the dependency on the control element (`.deck-automatic-link` element within `.deck-container`).
* **Allow a per-slide configuration of the slide delay** (for example through HTML5 `data-` attributes).


## Known issues
* Pausing on the last slide will only pause after it cycled back to the first slide (if cycle is enabled).
* Restarting from a pause on the one-before-last slide will cycle back to the first slide without playing the last one.

## License

MIT License

## Author

[Romain Champourlier](romain@softr.li)

[deck.js]: https://github.com/imakewebthings/deck.js