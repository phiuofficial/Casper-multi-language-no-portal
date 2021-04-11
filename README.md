# Casper multi-language and without subscription portal
This is an alternative version of Ghost's default theme Casper v. 4.0.4 (see below for more info).
The main purpose of this version is to enable multi-language text across Casper out of the box, for those people who are not familiar with coding.

I decided to develop this version of Casper for all non English creators, as it's weird to write all articles in a language and then having other areas of the website in English. This will open Ghost to a much wider public.

&nbsp;

# How to add a translation
Just take the file en.json from the locales folder and translate all instances on the right side of the ":" sign.
Please keep the "" and the comma at the end of each line
It would be great if you could upload your new language into the locales folder into this repository, so that the next Ghost user dealing with this issue will have it ready.

Example:

English version en.json
```
    "A collection of % posts": "A collection of % posts",
    "Back": "Back",
    "Enter your email": "Enter your email",
```

Italian translation (you have to Save as... "it.json" - or if you use another language, use the code for that language, e.g. "fr.json" for a French translation or "de.json" for a German one etc...)
```
    "A collection of % posts": "Una collezione di % post",
    "Back": "Indietro",
    "Enter your email": "Inserisci la tua email",
```

Finally, you have to set the language of your site to "it" in the General settings area of your Ghost control panel. Or "fr" in case of French language, "de" in case of German etc...

&nbsp;

# Subscription Portal
This version of Casper removes all subscription-related buttons and sections.
Main reasons:
* GDPR-related topics are not clear with Ghost as I am writing this, and I have seen many requests in the Ghost forum for disabing all subscription-related buttons and sections.
* It is not possible to translate subscription-related areas (onboarding, newsletter).

To complete the effort, you will have to:
1. Disable Google Analytics in your Ghost Settings
2. Add the following code into your Ghost "Code Injection" header section in the Settings menu:


```
<style>

.footer-cta {
    visibility: hidden;
    padding: 1vmin 1vmin 1vmin;
    }    
    
.footer-cta h2 {
    visibility: hidden;
    padding: 1vmin 1vmin 1vmin;
    }      

.footer-cta-button {
    visibility: hidden;
    padding: 1vmin 1vmin 1vmin;
    }         
    
.gh-portal-triggerbtn-iframe {
    visibility: hidden;
    }

</style>
```

To re-activate all the subscription-related sections:
1. delete the code above from the Code Injection section
2. in the default.hbs file, remove lines 54 and 62 (or just "uncomment" the lines in-between)


&nbsp;

And now the original Casper documentation:

# Casper

The default theme for [Ghost](http://github.com/tryghost/ghost/). This is the latest development version of Casper! If you're just looking to download the latest release, head over to the [releases](https://github.com/TryGhost/Casper/releases) page.

&nbsp;

![screenshot-desktop](https://user-images.githubusercontent.com/353959/66987533-40eae100-f0c1-11e9-822e-cbaf38fb8e3f.png)

&nbsp;

# First time using a Ghost theme?

Ghost uses a simple templating language called [Handlebars](http://handlebarsjs.com/) for its themes.

This theme has lots of code comments to help explain what's going on just by reading the code. Once you feel comfortable with how everything works, we also have full [theme API documentation](https://ghost.org/docs/themes/) which explains every possible Handlebars helper and template.

**The main files are:**

- `default.hbs` - The parent template file, which includes your global header/footer
- `index.hbs` - The main template to generate a list of posts, usually the home page
- `post.hbs` - The template used to render individual posts
- `page.hbs` - Used for individual pages
- `tag.hbs` - Used for tag archives, eg. "all posts tagged with `news`"
- `author.hbs` - Used for author archives, eg. "all posts written by Jamie"

One neat trick is that you can also create custom one-off templates by adding the slug of a page to a template file. For example:

- `page-about.hbs` - Custom template for an `/about/` page
- `tag-news.hbs` - Custom template for `/tag/news/` archive
- `author-ali.hbs` - Custom template for `/author/ali/` archive


# Development

Casper styles are compiled using Gulp/PostCSS to polyfill future CSS spec. You'll need [Node](https://nodejs.org/), [Yarn](https://yarnpkg.com/) and [Gulp](https://gulpjs.com) installed globally. After that, from the theme's root directory:

```bash
# install dependencies
yarn install

# run development server
yarn dev
```

Now you can edit `/assets/css/` files, which will be compiled to `/assets/built/` automatically.

The `zip` Gulp task packages the theme files into `dist/<theme-name>.zip`, which you can then upload to your site.

```bash
# create .zip file
yarn zip
```

# PostCSS Features Used

- Autoprefixer - Don't worry about writing browser prefixes of any kind, it's all done automatically with support for the latest 2 major versions of every browser.
- [Color Mod](https://github.com/jonathantneal/postcss-color-mod-function)


# SVG Icons

Casper uses inline SVG icons, included via Handlebars partials. You can find all icons inside `/partials/icons`. To use an icon just include the name of the relevant file, eg. To include the SVG icon in `/partials/icons/rss.hbs` - use `{{> "icons/rss"}}`.

You can add your own SVG icons in the same manner.


# Copyright & License

Copyright (c) 2013-2021 Ghost Foundation - Released under the [MIT license](LICENSE).
