# present.js

A(nother) custom JavaScript presentation script. I wrote this inspired by [slides.html5rocks.comπ](http://slides.html5rocks.com/) - but (a) didn't like the complexity in the script (obviously because those guys are doing a lot more than I needed to do) and (b) didn't like the navigation handling (back, forward, key controls, etc.).

Also - this all my own code, nothing pinched - I swear guvna!

Here's a simple example you can play with: [present.js demo](http://jsbin.com/oxohev/edit#html,live)

# Features

- Automatic sizing to browser window
- Supports predefined sizes
- Animated scrolling between slides can be enabled or disabled
- Linear view
- Full browser navigation supported (i.e. back and forward buttons)
- Permalinks - so you can jump to specific slide
- Doesn't *just* work in Chrome!

# Usage

Include present library:

    <link rel="stylesheet" href="present.css" type="text/css" />
    <script src="present.js"></script>

And you're ready to write your slides:

    <div class="slide">
      <!-- your awesome content -->
    </div>

The code is optimised for Chrome - simply because that's the browser I'm using right now, but it does also work in Firefox, Safari and Opera (though Opera doesn't currently support the CSS3 flex box model - so the content is in a odd place right now). 

Both keyboard and touch navigation allow you to move through the presentation: up/left, down/right, space/shift+space - for back and forth. Touch on the left side of the screen for back and right side for forward.

## Linear view

Press 't' to toggle between the linear view and the "slide" view. This should make it easier to skim through quickly if you're after something specific. 

Currently there's no print styles - that should be added and will look similar to the linear view.

## Resizing presentation

By default present.js will size to your window size. Alternatively you can specify a width and height:

    <script>
    present.resizeTo(800, 600); // 800x600
    </script>

## Enabling animated scroll

By default there's no animation to transition from one slide to the next. To do so, add the classname 'scroll' to the body element:

    <body class="scroll">

# Creating slides

Any element with a classname of "slide" will be read in as a slide. Typically this would be a `div` or perhaps a `section`:

    <div class="slide">
      <!-- your awesome content -->
    </div>

The slide is automatically assigned an id which can be referenced in the URL. If the slide has an id on it already, that will be used instead.

## Headings

An `h1` will sit firmly in the middle of the slide and is useful for slides containing only that content. Alternatively a `header` element will be put at the top of the slide for your content to sit inside. 

    <div class="slide">
      <h1>Welcome everyone!</h1>
    </div>

The text for the `h1`, `header` or other heading element is used for the slide title, which is displayed in the browser's title bar.

## Revealing individual blocks

If you want to reveal individual items on a slide, such as a list or some images, you can use the classname 'reveal':

    <div class="slide">
      <ul class="reveal">
        <li>Superted</li>
        <li>Spotty</li>
        <li>Texas Pete</li>
      </ul>
    </div>

Putting the reveal class on a `ul` or `ol` will automatically apply the reveal class to the `li` elements inside the list. If you wanted to start with the first `li` visible and reveal the subsequent items, you need to class the `li`s manually:

    <div class="slide">
      <ul>
        <li>Superted</li>
        <li class="reveal">Spotty</li>
        <li class="reveal">Texas Pete</li>
      </ul>
    </div>

## Realing with a fade

Elements with a reveal class are hidden using the following style:

    visibility: hidden;
    opacity: 0;

Adding a classname of 'fade' to the reveal element will animate the opacity on reveal (using CSS3 transitions).

## The current item revealed

Out of all the elements with a reveal class on the slide, the *current* item being revealed will have a classname of 'current'. You can use this to style the element different if you wanted.