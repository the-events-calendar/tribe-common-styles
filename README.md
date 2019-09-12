# Tribe Common Styles

## What is this repository?

This repository is a set of common PostCSS utilities. It includes variables, icons, and mixins to help follow Modern Tribe products design system. They are consumed by Modern Tribe plugins PostCSS files.

## Why do we need this?

Modern Tribe has a design system for its plugins. Defining a set of variables and style groupings helps maintain consistency and ease of maintenance throughout all the plugins.

For example, if the primary text color was to change due to a design update, doing a search and replace through all the PostCSS files could be time-consuming and error-prone. Instead, changing it in one place changes the color for all styles consuming the variable.

## Repository Structure

The repository structure starts at the root level file `_all.pcss` importing all the repository styles. Variables, icons, and mixins are defined within their respective folders.

### Variables

Variables are any *reusable* property values named specifically for their use case. They are found in the `/variables` folder. Though some variables may hold the same value (e.g. `--border-radius-default: 4px;` and `--spacer-0: 4px`), their use cases are very different and should not be used interchangeably.

SVGs are different from the other variables partial files. They are found in `/variables/_svgs.pcss` and are compiled using the [PostCSS Inline SVG](https://github.com/TrySound/postcss-inline-svg) plugin.

### Icons

Icons are SVG icons included in the design system and are found in the `/icons` folder. They are consumed by the SVG variables partial file `/variables/_svg.pcss`.

### Mixins

Mixins are groupings of *reusable* styles and are found in the `/mixins` folder. These reusable style groupings are often defined by the design system. Mixins are compiled using the [PostCSS Mixins](https://github.com/postcss/postcss-mixins) plugin.

## Making Changes

Making changes to this repository should be done with care. As these utilities are the most upstream in Modern Tribe products PostCSS files, modifications to these files can have a cascading effect downstream.

When making any changes, whether they are additions, alterations, or deletions, **consistency** is key. Follow naming conventions and groupings so that viewing and editing the files are simple.

### Additions

Additions are generally safe, as long as the variable names do not conflict with existing variables. Confirm that the variables or mixins you are adding are reusable and a consistent part of the design system before adding.

### Alterations

Alterations should be done carefully, as they will affect all downstream styles using the variable or mixin being altered. Multiple plugins use these styles and should be cross-checked before making the change.

### Deletions

Deletions should also be done carefully, for the same reasons as **Alterations** above. Removing a variable or mixin that is still being used will create broken styles and/or build failures.

## Installation

You probably will need to install this package in a custom paths, say `src/resources/postcss/utilities`; if that's the case then add this to the plugin/project `composer.json` file:

```json
  "repositories": [
    {
      "name": "moderntribe/tribe-common-styles",
      "type": "github",
      "url": "https://github.com/moderntribe/tribe-common-styles",
      "no-api": true
    }
  ],
  "extra": {
    "installer-paths": {
      "src/resources/postcss/utilities": [
        "moderntribe/tribe-common-styles"
      ]
    }
  }
```
To simply install the package in your project use:

```bash
composer require --dev moderntribe/tribe-common-styles
```

## Source installation

If you need to work on **this** package while working on your project you will want to clone the full Git repository, just follow the instructions above and, in place of the command above, use:

```bash
composer require --dev moderntribe/tribe-common-styles --prefer-source
```

Remember to ignore the package installation folder to avoid committing a dirty repository!
