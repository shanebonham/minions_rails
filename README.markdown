# MinionsRails

This is a Rails wrapper for the [minions.css](https://github.com/chantastic/minions.css) project.

## Contents
1. [Installation](#installation)
1. [Important](#important)
1. [About minions](#about-minions)
1. [CSS vs SCSS](#css-vs-scss)
1. [Usage](#usage)
  1. [CSS (development)](#css-development)
  1. [CSS (production)](#css-production)
  1. [SCSS (development)](#scss-development)
  1. [SCSS (production)](#scss-production)
1. [Mixins](#mixins)
  1. [at](#at)
  1. [before](#before)
  1. [only](#only)
  1. [exclude](#exclude)

## Installation
**Add** `minions_rails` to your Gemfile and bundle:

```ruby
gem 'minions_rails'
```

## Important
[minions.css](https://github.com/chantastic/minions.css) is a huge library. There's nearly 1MB of CSS. It's not intended to be used segmentally. The `development` setups are included so you can get started quickly. Please don't use them in production.

## About minions
For more information about [minions.css](https://github.com/chantastic/minions.css), go to the library page: https://github.com/chantastic/minions.css

## CSS vs SCSS
**The `scss` version of [minions.css](https://github.com/chantastic/minions.css) allows you to customize media-query berakpoints.** By default, [minions.css](https://github.com/chantastic/minions.css) uses the Bootstrap 4 breakpoints. They look like this:

```
@xl: 1200px
@lg:  992px
@md:  768px
@sm:  544px
@xs:  320px
```

## Usage

### CSS (development)
This is an easy setup to get you up and running quickly. But it's a lot of CSS to load in production.  

[Working example](https://github.com/chantastic/minions_rails/blob/master/test/dummy/app/assets/stylesheets/css_development.css)

* **Require** `minions_rails/development` in your `application.css` file:

```css
*= require "minions_rails/development"
```

**[DO NOT USE THIS IN PRODUCTION](#important).**

---

### CSS (production)
This is what a production setup might look like. Note that this is a `.scss` file. You could use sprockets if you like, but it'll result in a bunch of HTTP requests in development. They add up, if you're using a lot of minions.  

I still consider it a CSS setup because you're using the raw CSS minions. These files aren't dynamic.  

[Working example](https://github.com/chantastic/minions_rails/blob/master/test/dummy/app/assets/stylesheets/css_production.scss)

* **Create** a `custom-minions.scss` file
  + **Import** any and all minions files from `minions_rails/css/`

```scss
/* custom-minions.scss */

@import "minions_rails/css/padding";
@import "minions_rails/css/padding-mn";
@import "minions_rails/css/padding-xs";
@import "minions_rails/css/padding-sm";
@import "minions_rails/css/padding-md";
@import "minions_rails/css/padding-lg";
@import "minions_rails/css/padding-xl";

/* ... so on and so forth. */
```

---

### SCSS (development)
This is an easy setup to get you up and running with custom breakpoints. But it's a lot of CSS to load in production.  

[Working example](https://github.com/chantastic/minions_rails/blob/master/app/assets/stylesheets/minions_rails/development-scss.scss)

* **Create** a `custom-minions.scss` file
  + **Assign** expected breakpoint variables `$xl`, `$lg`, `$md`, `$sm`, and `$xs`
  + **Assign** colors, if using any of the `color` files.
    -  `$white`, `$navy`, `$blue`, `$aqua`, `$teal`, `$olive`, `$green`, `$lime`, `$yellow`, `$orange`, `$red`, `$maroon`, `$fuchsia`, `$purple`, `$gray`, `$silver`, `$black`
  + **Import** any and all minions files from `minions_rails/scss/`
* **Require** `custom-minions` into your `application.css` file

```scss
$xl: 1200;
$lg:  960;
$md:  720;
$sm:  600;
$xs:  480;

$white: #ffffff;
$navy: #001f3f;
$blue: #0074d9;
$aqua: #7fdbff;
$teal: #39cccc;
$olive: #3d9970;
$green: #2ecc40;
$lime: #01ff70;
$yellow: #ffdc00;
$orange: #ff851b;
$red: #ff4136;
$maroon: #85144b;
$fuchsia: #f012be;
$purple: #b10dc9;
$gray: #aaaaaa;
$silver: #dddddd;
$black: #111111;

@import "minions_rails/development-scss";
```

**[DO NOT USE THIS IN PRODUCTION](#important).**

---

### SCSS (production)
This is the most customizable setup. You can control both the minions you use and the breakpoints they operate on.

[Working example](https://github.com/chantastic/minions_rails/blob/master/test/dummy/app/assets/stylesheets/scss_production.scss)

* **Create** a `custom-minions.scss` file
  + **Assign** expected breakpoint variables `$xl`, `$lg`, `$md`, `$sm`, and `$xs`
  + **Import** any and all minions files from `minions_rails/scss/`
* **Require** `custom-minions` into your `application.css` file

```scss
/* custom-minions.scss */

$xl: 1200;
$lg:  960;
$md:  720;
$sm:  600;
$xs:  480;

$white: #ffffff;
$navy: #001f3f;
$blue: #0074d9;
$aqua: #7fdbff;
$teal: #39cccc;
$olive: #3d9970;
$green: #2ecc40;
$lime: #01ff70;
$yellow: #ffdc00;
$orange: #ff851b;
$red: #ff4136;
$maroon: #85144b;
$fuchsia: #f012be;
$purple: #b10dc9;
$gray: #aaaaaa;
$silver: #dddddd;
$black: #111111;

@import "minions_rails/scss/padding";
@import "minions_rails/scss/padding-mn";
@import "minions_rails/scss/padding-xs";
@import "minions_rails/scss/padding-sm";
@import "minions_rails/scss/padding-md";
@import "minions_rails/scss/padding-lg";
@import "minions_rails/scss/padding-xl";

/* ...and whatever else you need */
```

## Mixins
Interfaces ships with a bunch of mixins so you can style your classes with the same constraints minions uses.

### at()
[The code](https://github.com/chantastic/minions_rails/tree/master/app/assets/stylesheets/minions_rails/mixins/at.scss)  
[Example use](https://github.com/chantastic/minions_rails/tree/master/test/dummy/app/assets/stylesheets/at_mixin.scss)  

---

### before()
[The code](https://github.com/chantastic/minions_rails/tree/master/app/assets/stylesheets/minions_rails/mixins/before.scss)  
[Example use](https://github.com/chantastic/minions_rails/tree/master/test/dummy/app/assets/stylesheets/before_mixin.scss)  

---

### only()
[The code](https://github.com/chantastic/minions_rails/tree/master/app/assets/stylesheets/minions_rails/mixins/only.scss)  
[Example use](https://github.com/chantastic/minions_rails/tree/master/test/dummy/app/assets/stylesheets/only_mixin.scss)  

---

### exclude()
[The code](https://github.com/chantastic/minions_rails/tree/master/app/assets/stylesheets/minions_rails/mixins/exclude.scss)  
[Example use](https://github.com/chantastic/minions_rails/tree/master/test/dummy/app/assets/stylesheets/exclude_mixin.scss)  


---

<3 [chantastic](http://twitter.com/chantastic)

This project rocks and uses MIT-LICENSE.
