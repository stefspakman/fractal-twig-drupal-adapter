# Twig Adapter

An adapter to let you use [Twig](https://github.com/twigjs/twig.js) templates with [Fractal](http://github.com/frctl/fractal). Forked from [wearewondrous/fractal-twig-drupal-adapter](https://github.com/wearewondrous/fractal-twig-drupal-adapter)

## Installation

```bash
$ npm install --save @goat-cli/fractal-twig-adapter
```

in your `fractal.js`

```js
const fractal = require('@frctl/fractal').create();
const twigAdapter = require('@goat-cli/fractal-twig-adapter');
const twig = twigAdapter({
  nameSpaces: {
    atoms: '01-atoms',
    molecules: '02-molecules',
    organisms: '03-organisms',
    templates: '04-templates',
    pages: '05-pages',
  },
});

fractal.components.engine(twig);
fractal.components.set('ext', '.twig'); 
```

## Usage

This adapter allows you to use some Drupal filters, functions and tags.

### Supported Filters

`|t` - The Drupal core translation filter. Additional parameters not supported, yet.

`|field_value` - Provided by the module [drupal/twig_field_value](https://www.drupal.org/projects/twig_field_value) to use plain outputs from a field.

#### Add Custom Filters, functions, tests and tags

You have the ability to extend Twig with custom filters, functions, tests and tags by passing a function to the twig adapter as follows:

```js
const twig = twigAdapter({
  filters: {
    render(str) {
      return str;
    }
  }
});
```
 For example the a filter: the name of the function will be used as the filter name (eg: `|render`).

### Supported Functions

`path()` - The Drupal core path function.

`url()` - The Drupal core url function.

`block_view()` - Provided by the module [drupal/twig_extender](https://www.drupal.org/projects/twig_extender) to directly print a block.

### Supported tags

`{% trans %}` - The Drupal core translate tag.

## Original Creator

[WONDROUS](https://www.wearewondrous.com/)

[MIT License](LICENSE)
