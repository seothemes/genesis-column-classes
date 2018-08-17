# Genesis Column Classes

Add Genesis column classes CSS to your project through Node.

## SCSS

This package also contains an SCSS version of the styles with helpful variables and mixins.

### Variables

The `$genesis-columns-breakpoint` variable can be overridden in your project. This is the minimum screen size at which the column widths should be applied.

```scss
$genesis-columns: (
	margin: 2.564102564102564%,
	one-half: 48.71794871794871%,
	one-third: 31.62393162393162%,
	one-fifth: 17.94871794871794%,
	one-fourth: 23.07692307692307%,
	one-sixth: 14.52991452991453%,
	one-seventh: 12.08791208791208%,
	one-eighth: 10.25641025641025%,
	one-ninth: 8.831908831908832%,
	two-thirds: 65.81196581196582%,
	two-fourths: 48.71794871794871%,
	two-fifths: 38.46153846153846%,
	two-sixths: 31.62393162393162%,
	three-fourths: 74.35897435897436%,
	three-fifths: 58.97435897435897%,
	three-sixths: 48.71794871794871%,
	four-fifths: 79.48717948717948%,
	four-sixths: 65.81196581196582%,
	five-sixths: 82.90598290598291%,
);
```

Variables can be called with the `map-get` function. For example:

```scss
.footer-widget-area {
    width: map_get($genesis-columns, one-third);
}
```

# Mixins

```scss
@mixin genesis-column($width: null, $first: null) {
	clear: if($first, both, none);
	margin-left: if($first, 0, map_get($genesis-columns, margin));

	@if null != $width {
		float: left;
		width: map_get($genesis-columns, $width);
	}
}
```

To use the `genesis-column` mixin, simply enter the column class as the width argument and optionally pass in the second argument, e.g:

```scss
.footer-widget-area {
    @include genesis-column(one-third);
    
    &:nth-of-type(1) {
        @include genesis-column(null, first);
    }
}
```


