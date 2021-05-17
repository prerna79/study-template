# Rally + WebScience Study Template
This repository provides a template for building browser-based research studies with the [Rally](https://rally.mozilla.org/) platform and the [WebScience](https://github.com/mozilla-rally/web-science/) library.

## Background Material

Before working with this template, we recommend familiarizing yourself with the following concepts.

* Implementing Research Studies as Browser Extensions
  * [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction) - The scripting language commonly used for web applications, including browser extensions. Studies on Rally are implemented in JavaScript. If you haven't worked with JavaScript in awhile, we especially recommend catching up on [modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules), [promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise), and [web workers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers), since those features are used in Rally, WebScience, and this template.
  * [WebExtensions](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions) - An API for building browser extensions. Each study on Rally is a separate extension. If you haven't worked with WebExtensions in awhile, we recommend reviewing the [structure of browser extensions](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Anatomy_of_a_WebExtension), including [manifests](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json), [background scripts](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Anatomy_of_a_WebExtension#background_scripts) which run in a background page, and [content scripts](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Content_scripts) which run on ordinary pages.
  * [WebScience](https://github.com/mozilla-rally/web-science/) - A library for building browser-based research studies. WebScience provides production-quality functionality that is commonly required, difficult to implement correctly, and difficult to maintain.
  * [Rally.js](https://github.com/mozilla-rally/rally-core-addon/tree/master/support) - A library for integrating your study with the Rally platform. Rally.js communicates with a separate Rally core extension, which manages user enrollment and submits telemetry pings.
* Building and Testing Research Study Browser Extensions
  * [ESLint](https://eslint.org/) - A linter for JavaScript. This template invokes ESLint with Node.js commands; you should not have to manually run ESLint or modify the ESLint configuration.
  * [Node.js](https://nodejs.org/) - A JavaScript runtime for web applications. This template uses Node.js in two primary ways. First, Node.js provides a convenient toolkit for managing JavaScript library dependencies (see [`npm`](https://docs.npmjs.com/cli/v7/commands/npm) and [`package.json`](https://docs.npmjs.com/cli/v7/configuring-npm/package-json)). You can easily integrate Node.js packages from the [npm public registry](https://www.npmjs.com/). Second, Node.js enables running build and test commands that are similar to makefile targets (see [package scripts](https://docs.npmjs.com/cli/v7/using-npm/scripts) and [`npm run`](https://docs.npmjs.com/cli/v7/commands/npm-run-script)). You should not have to modify these Node.js commands. Note that this template does _not_ use Node.js as a runtime for research studies.
  * [Rollup](https://rollupjs.org/) - A module bundler for JavaScript. This template uses Rollup to merge module dependencies (either your own modules or npm modules) into a study extension and to remove unused code from dependencies. The template also enables using module depencies in content and worker scripts. You should not have to modify the Rollup configuration of the template.
  * [web-ext](https://extensionworkshop.com/documentation/develop/getting-started-with-web-ext/) - A toolkit for building and testing browser extensions. This template invokes web-ext with Node.js commands; you should not have to modify the web-ext configuration.

## Template Contents

This template includes the following files.

* [`.eslintignore`](./eslintignore) and [`.eslintrc`](./eslintrc) - ESLint configuration. You should not have to modify these files.
* [`.gitignore`](./gitignore) - Git configuration. You should not not have to modify this file.
* [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md) - The [code of conduct](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/adding-a-code-of-conduct-to-your-project) for the study extension. You should update this file to reflect your code of conduct.
* [`LICENSE`](./LICENSE) - The [license](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/licensing-a-repository) for the study extension. You can use the provided license or your own license, so long as your license is compatible with Rally requirements and the licenses of dependencies.
* [`README.md`](./README.md) - A [README](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/about-readmes) for the study extension. You should update this file to describe your study and its implementation.
* [`manifest.json`](./manifest.json) - A WebExtensions [manifest](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json) for the study. You should update the [`description`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/description), [`author`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/author), [`name`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/name), [`version`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/version), and [`homepage_url`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/homepage_url) fields for your study. You can also update [`permissions`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/permissions) as necessary for implementing your study. The Rally team will provide a value for the [`browser_specific_settings.gecko.id`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/browser_specific_settings) field.
* [`package.json`](./package.json) - A Node.js [package configuration](https://docs.npmjs.com/cli/v7/configuring-npm/package-json) for the study. You should update the `name`, `version`, `description`, `repository`, `keywords`, `author`, `license`, `bugs`, and `homepage` fields. You should not have to update the `scripts` field, which specifies a set of commands that function like makefile targets. You can add `dependencies` for your study implementation, either manually or with `npm install`. Note that you must use [`npm install`](https://docs.npmjs.com/cli/v7/commands/npm-install) to install dependencies and [`npm update`](https://docs.npmjs.com/cli/v7/commands/npm-update) to update dependencies.
* [`package-lock.json`](./package-lock.json) - A file automatically generated by Node.js package management that [describes package dependencies](https://docs.npmjs.com/cli/v7/configuring-npm/package-lock-json). You should not have to manually edit this file.
* [`rollup.config.js`](./rollup.config.js) - A [Rollup](https://rollupjs.org/) configuration for the study. You should not have to modify this file.
* [`web-ext-config.js`](./web-ext-config.js) - A [web-ext](https://extensionworkshop.com/documentation/develop/getting-started-with-web-ext/) configuration for the study. This configuration will, on browser startup, automatically open both the [Browser Console](https://developer.mozilla.org/en-US/docs/Tools/Browser_Console) and [Firefox Developer Tools](https://developer.mozilla.org/en-US/docs/Tools) for the background page. You should not have to modify this file.
* `.circleci/` - CircleCI configuration.
  * `config.yml` - A basic CircleCI configuration for the study template. You can use this file as a starting point for your own tests, or you can safely remove the file.
* `.github/` - GitHub configuration.
  * `dependabot.yml` - A [GitHub dependency update](https://docs.github.com/en/code-security/supply-chain-security/keeping-your-dependencies-updated-automatically) configuration. You can use this file for managing dependency updates, or you can safely remove the file.
* `src/` - The source for the study implementation. You should include all your study JavaScript files in this directory, and you can optionally include non-JavaScript assets. The build system will bundle JavaScript files to the `/dist` directory, as described below. The build system will also copy non-JavaScript assets (i.e., any files that do not end in `.js`) to the `dist/` directory.
  * `background.js` - The main [background script](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Anatomy_of_a_WebExtension#background_scripts) for the study. The build system will bundle this script and output to `dist/background.js`. Note that the WebExtensions manifest already specifies `dist/background.js` as a background script for the extension.
  * `exampleContentScript.content.js` - An example [content script](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Content_scripts) for the study. The build system automatically recognizes a `*.content.js` file as a content script, bundles it separately from the main background script, and outputs to the same relative path in `dist/` that the file has in `src/`. The build system will output this content script file, for example, to `dist/exampleContentScript.content.js`. We provide this functionality so that study content scripts can include module dependencies.
  * `exampleModule.js` - An example module for the study. The build system will bundle this module into the main background script; there is no separate output in `dist/`. If you want to split your background script implementation into multiple files, we recommend using modules imported into `background.js` to benefit from performance optimizations in bundling, rather than using multiple background scripts specified in `manifest.json`.
  * `exampleWorkerScript.worker.js` - An example web worker script for the study. The build system treats `*.worker.js` files the same way as `*.content.js` files.
* `tests/integration/` - A basic [Selenium](https://www.selenium.dev/) integration test for the study template. You can use these files as a starting point for your own tests, or you can safely remove the files.

## Getting Started

Prerequisites: current versions of [Firefox](https://www.mozilla.org/firefox/new/) and [Node.js](https://nodejs.org/). You might find it helpful to install Node.js with a [package manager](https://nodejs.org/en/download/package-manager/), such as [Scoop](https://scoop.sh/) on Windows, [Homebrew](https://brew.sh/) on macOS, or [`apt-get`](https://help.ubuntu.com/community/AptGet/Howto) on Ubuntu Linux.
1. [Fork](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo) this repository.
2. Update the [WebExtensions manifest](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json) ([`manifest.json`](./manifest.json)) for your study. You should update the [`description`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/description), [`author`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/author), [`name`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/name), [`version`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/version), and [`homepage_url`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/homepage_url) fields. The Rally team will provide a value for the [`browser_specific_settings.gecko.id`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/browser_specific_settings) field.
3. Update the [Node.js package configuration](https://docs.npmjs.com/cli/v7/configuring-npm/package-json) ([`package.json`](./package.json)) for your study. You should update the `name`, `version`, `description`, `repository`, `keywords`, `author`, `license`, `bugs`, and `homepage` fields.
4. In the forked repository, run [`npm install`](https://docs.npmjs.com/cli/v7/commands/npm-install) to install Node.js package dependencies. A new `node_modules/` directory will be automatically populated with these dependencies.
5. Run `npm run start-dev`. The build system will build your study extension, launch Firefox with the study extension installed, and automatically open both the [Browser Console](https://developer.mozilla.org/en-US/docs/Tools/Browser_Console) and [Firefox Developer Tools](https://developer.mozilla.org/en-US/docs/Tools) for the background page.
6. Commit your study extension to a repository! You now have a clean and functional starting point for implementing your study. If this template is updated in future, you can also easily merge those updates into your study.

## Build System Commands
This template comes with a set of predefined Node.js commands, which function similar to makefile targets. These commands should help you with study implementation, debugging, testing, and deployment. You run each command with `npm run <command>`.

* `build` - Builds the study extension, by bundling JavaScript implementation in `src/` and copying non-JavaScript files. Output is in the `dist/` directory.
* `dev` - Bundles the study extension (like `build`), but in _developer mode_. In developer mode, Rally.js ignores whether the Rally core extension is installed and outputs telemetry pings to the [Browser Console](https://developer.mozilla.org/en-US/docs/Tools/Browser_Console). Developer mode also provides a [source map](https://developer.mozilla.org/en-US/docs/Tools/Debugger/How_to/Use_a_source_map) for bundled JavaScript, so you can use the [Debugger](https://developer.mozilla.org/en-US/docs/Tools/Debugger) as if the JavaScript were not bundled. You should typically use developer mode when implementing and testing your study.
* `lint`: Run linting on the study extension.
* `package`: Build the study extension (`build`), then package the built study into an archive for distribution. Output is in the `web-ext-artifacts/` directory.
* `start`: Build the study extension (`build`), then launch Firefox with the study extension installed.
* `start-dev`: Build the study extension in _developer mode_ (`dev`), then launch Firefox with the study extension installed.
* `test-integration`: Packages the study extension (`package`), then runs the provided integration test.
* `watch`: Build the study extension in _developer mode_ (`dev`), launch Firefox with the study extension installed, automatically rebuild the study if a file changes, and automatically reload the study in Firefox if the study is rebuilt. You should typically use `watch` for study extension testing and debugging.

## Debugging the Study Extension in Firefox
* Debugging the Background Script - Navigate to the browser debugging page (`about:debugging`), click This Firefox, then click Inspect on the study extension. The page that opens is [Firefox Developer Tools](https://developer.mozilla.org/en-US/docs/Tools) for the background page, including a [Web Console](https://developer.mozilla.org/en-US/docs/Tools/Web_Console), [JavaScript Debugger](https://developer.mozilla.org/en-US/docs/Tools/Debugger), and [Network Monitor](https://developer.mozilla.org/en-US/docs/Tools/Network_Monitor). Background script console output will also appear on the [Browser Console](https://developer.mozilla.org/en-US/docs/Tools/Browser_Console). The template's web-ext configuration will automatically open both Firefox Developer Tools for the background page and the Browser Console on browser startup.
* Debugging a Content Script - On a page where the content script is running, open [Firefox Developer Tools](https://developer.mozilla.org/en-US/docs/Tools). The [Web Console](https://developer.mozilla.org/en-US/docs/Tools/Web_Console) will include output from the content script, and you can select the content script in the [JavaScript Debugger](https://developer.mozilla.org/en-US/docs/Tools/Debugger). Content script console output will also appear on the [Browser Console](https://developer.mozilla.org/en-US/docs/Tools/Browser_Console).
