# Search: A Plugin for Pelican

[![Build Status](https://img.shields.io/github/workflow/status/pelican-plugins/search/build)](https://github.com/pelican-plugins/search/actions)
[![PyPI Version](https://img.shields.io/pypi/v/pelican-search)](https://pypi.org/project/pelican-search/)

Serialize generated HTML content to a JS variable for static site searches.


## Installation

This plugin can be installed via:

    python -m pip install pelican-search


## Why do you need it?

Static sites do not offer search feature out of the box. [Tipue Search](https://web.archive.org/web/20200703134724/https://tipue.com/search/)
is a jQuery plugin that search the static site without using any third party service, like DuckDuckGo or Google.

Tipue Search requires the textual content of site in a JS variable.


## How Tipue Search works

Tipue Search serializes the generated HTML into JSON and saves it into a JS variable. Format of JSON is as follows

```javascript
var tipuesearch = {
    "pages": [
        {
            "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet. Duis sagittis ipsum. Praesent mauris. Fusce nec tellus sed augue semper porta. Mauris massa. Vestibulum lacinia arcu eget nulla. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Curabitur sodales ligula in libero.",
            "tags": "Example Category",
            "url" : "http://oncrashreboot.com/plugin-example.html",
            "title": "Everything you want to know about Lorem Ipsum"
        },
        {
            "text": "Sed dignissim lacinia nunc. Curabitur tortor. Pellentesque nibh. Aenean quam. In scelerisque sem at dolor. Maecenas mattis. Sed convallis tristique sem. Proin ut ligula vel nunc egestas porttitor. Morbi lectus risus, iaculis vel, suscipit quis, luctus non, massa. Fusce ac turpis quis ligula lacinia aliquet. Mauris ipsum. Nulla metus metus, ullamcorper vel, tincidunt sed, euismod in, nibh.",
            "tags": "Example Category",
            "url" : "http://oncrashreboot.com/plugin-example-2.html",
            "title": "Review of the book Lorem Ipsum"
        }
    ]
};
```

JS variable is written to file `tipuesearch_content.js` which is created in the root of `output` directory.


## How to use

Your theme needs to have Tipue Search properly configured in it. [Official documentation](https://web.archive.org/web/20200703134724/https://tipue.com/search/help/) has the required details.

In addition to the instructions from Tipue Search, the following has to be added in `pelicanconf.py`.

```python
PLUGIN_PATH = 'plugins'
PLUGINS = ['search']
DIRECT_TEMPLATES = ['index', 'tags', 'categories', 'authors', 'archives', 'search']
```

Furthermore, the generated JavaScript variable has to be sourced in the relevant html pages.

```html
<script src="{{ SITEURL }}tipuesearch_content.js"></script>
```

Pelican [Plumage theme](https://github.com/kdeldycke/plumage) has Tipue Search configured. Check our its code to understand the configuration.


## Backward Compatibility

This plugin requires Tipue Search Version 7.0 or higher.

Tipue Search used to expect content in a json file. Around Version 7.0, Tipue Search made a switch to JavaScript variable. This plugin was updated to reflect this change in commit `4a5f171fc`. Latest version of this plugin will not work with older versions of Tipue Search.

If you are using older Tipue Search, prior to 7.0 release, then you will find old version of this plugin in commit `2dcdca8c8`.


## Source Archive

The Tipue Search project itself seems to have been long abandonned. There is no
longer any official canonical reference of source code or documentation. There
only some artifacts left that were archived by the community:

* [Archived Tipue Search homepage](https://web.archive.org/web/20200703134724/https://tipue.com/search/)
* [Archived Tipue plugin help page](https://web.archive.org/web/20200703134724/https://tipue.com/search/help/)
* [Archived Tipue Search code v7.1](https://web.archive.org/web/20200703134724/https://www.tipue.com/search/tipuesearch.zip)
* [GitHub repository copy](https://notabug.org/jorgesumle/Tipue-Search)


## Contributing

Contributions are welcome and much appreciated. Every little bit helps. You can contribute by improving the documentation, adding missing features, and fixing bugs. You can also help out by reviewing and commenting on [existing issues][].

To start contributing to this plugin, review the [Contributing to Pelican][] documentation, beginning with the **Contributing Code** section.

[existing issues]: https://github.com/pelican-plugins/search/issues
[Contributing to Pelican]: https://docs.getpelican.com/en/latest/contribute.html
