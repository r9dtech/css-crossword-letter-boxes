# CSS Crossword Letter Boxes

Provides CSS for wrapping each letter in an HTML element in a box.

The functionality is in `css-crossword-letter-boxes.css`, with a demo in `index.html`.

## Usage

To use, import `css-crossword-letter-boxes.css` apply the class `css-crossword-letter-boxes` to your element.

### Block elements

For block elements (or any element with a specified width), it is important to set the width to a multiple of the
`line-height`:

```html
<style>
	#my-div {
		width: 6lh;
	}
</style>
<div
	id="my-div"
	class="css-crossword-letter-boxes"
>
	sample
</div>
```

### Input elements

Like block elements, input elements also need the width to be specified, and be a multiple of `line-height`.

If the input has a maximum length, then you may want the width to be one `lh` longer than `maxlength` so that the
content doesn't scroll.

Additionally, you should disable the browser's default styling for rendering for input boxes.

```html

<style>
	#my-input {
		width: 11lh;
		appearance: none /* remove default browser styling */;
		border: none /* remove default border */;
	}
</style>
<input
	id="my-input"
	class="css-crossword-letter-boxes"
	maxlength="10"
/>
```

### Inline elements

Inline elements include the trailing letter spacing, so need to be clipped using an extra class:

```html
<span class="css-crossword-letter-boxes css-crossword-letter-boxes-clip"
	>test</span
>
```

### Box size

The size of the boxes is dictated by the `line-height` of an element, so you can set the box size using:

```css
.css-crossword-letter-boxes {
	line-height: 1.5em;
}
```

### Font

The `css-crossword-letter-boxes` class uses `monospace`, but you can override this in your own css:

```css
.css-crossword-letter-boxes {
	font-family: "Ubuntu Mono", monospace;
}
```

It is important to have 'monospace' as the fallback font.

### Styling the boxes

You can override the line width, line color, and background color:

```html
<style>
	#my-span {
		--css-crossword-letter-boxes--line-width: 2px;
		--css-crossword-letter-boxes--line-color: red;
		--css-crossword-letter-boxes--background-colour: aliceblue;

		&:hover {
			--css-crossword-letter-boxes--background-colour: deepskyblue;
		}
	}
</style>
<span
	id="my-span"
	class="css-crossword-letter-boxes css-crossword-letter-boxes-clip"
	>example</span
>
```

## Limitations

### 16-character limit

This limit is arbitrary, and can be made higher by editing the css.

Unfortunately (at the time of writing) there seems to be no way to render these boxes nicely in pure-css with
arbitrarily many characters. Boxes can be drawn with repeating linear gradients, but the result is not pixel perfect.

### Font choice

You must use a monospace font, otherwise the boxes won't render correctly.

### Browser support

This will only work on relatively recent browsers supporting features like `var` and `calc`.

### Padding and box-sizing

This will only work if you don't override certain css properties, such as `padding`, `box-sizing`, and `clip-path`.
