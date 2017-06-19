# Extended Css engine
[![Build Status](https://travis-ci.org/AdguardTeam/ExtendedCss.svg?branch=master)](https://travis-ci.org/AdguardTeam/ExtendedCss)

Module for applying CSS styles with extended selection properties.

These extended properties are defined in the following github issues:

Selector property | Description
--- | ---
`-ext-has (:has)` | https://adguard.com/en/filterrules.html#pseudo-class-has
`-ext-contains (:contains)` | https://adguard.com/en/filterrules.html#pseudo-class-contains
`-ext-matches-css (:matches-css)` | https://adguard.com/en/filterrules.html#pseudo-class-matches-css

### Usage
```
(function() {
  var cssText = 'div.wrapper>div[-ext-has=".banner"] { display:none!important; }\n';
  cssText += 'div.wrapper>div[-ext-contains="some word"] { background:none!important; }';
  var extendedCss = new ExtendedCss(cssText);
  extendedCss.apply();
  
  // Just an example of how to stop applying this extended CSS
  setTimeout(function() {
    extendedCss.dispose();
  }, 10 * 1000);
})();
```

### Debugging extended selectors

[Here](https://AdguardTeam.github.io/ExtendedCss/dist/bookmarklet.html) is a bookmarklet that loads ExtendedCss to the page. You can use the `ExtendedCss` constructor in a global scope, and its method `ExtendedCss.query` as `document.querySelectorAll`.

```
var selectorText = "div.block[-ext-has='.header:matches-css-after(content: \"Anzeige\")']";

ExtendedCss.query(selectorText) // returns an array of Elements matching selectorText
```
