# Oh My Console

[![NPM version](https://img.shields.io/npm/v/oh-my-console.svg?style=flat)](https://www.npmjs.org/package/oh-my-console)
[![Build Status](https://travis-ci.org/psfe/oh-my-console.svg?branch=master&foo)](https://travis-ci.org/psfe/oh-my-console)
[![Coverage Status](https://coveralls.io/repos/github/psfe/oh-my-console/badge.svg?branch=master&foo)](https://coveralls.io/github/psfe/oh-my-console?branch=master)
[![Dependency manager](https://img.shields.io/david/psfe/oh-my-console.svg?style=flat)](https://david-dm.org/psfe/oh-my-console)

Shell:

<img width="500" alt="shell" src="https://cloud.githubusercontent.com/assets/4427974/18906370/e5d7cafc-8599-11e6-8c98-6bb7f7dbaec9.png">

Browser:

<img width="500" alt="browser" src="https://cloud.githubusercontent.com/assets/4427974/18906374/e81c1dae-8599-11e6-92e9-37db35ee8a2a.png">

## Installation

### Node.js

```bash
npm install oh-my-console
```

### Browser

```html
<script>window.DEBUG="main"</script>
<script src="dist/oh-my-console.min.js"></script>
```

## Usage

### Node.js

```javascript
var logger = require('oh-my-console')('main:foo');

logger.log('bar');
// Output:
// [<timestamp>][main:foo] bar

logger.debug('bar')
// Output only when DEBUG equals "main" or "main:foo"
// [<timestamp>][main:foo] bar
```

A demo can be found [here](demo/node).
 
### AMD

[dist/oh-my-console](dist/oh-my-console.min.js) supports AMD envirenment,
as long as loaded into your HTML:

```javascript
window.DEBUG = "main";
require(['OhMyConsole'], function(Logger) {
    var logger = Logger('main:sub');

    logger.log('some information');
    logger.error('there was an error');
    logger.debug('matches DEBUG: main, main:sub');
});
```

A demo can be found [here](demo/browser/amd.html).
 
### Global Object for Browser

[dist/oh-my-console](dist/oh-my-console.min.js) **will** export a
`window.OhMyConsole` object if there's no `require` or `module` defined.

```javascript
window.DEBUG = "main";
var logger = window.OhMyConsole('main:sub');

logger.log('some information');
logger.error('there was an error');
logger.debug('matches DEBUG: main, main:sub');
```

A demo can be found [here](demo/browser/global.html).

## API

### logger.debug

debug output respect to `process.env.DEBUG` or `window.DEBUG`.

### logger.info

info level output implemented by `console.info`.

### logger.log

log level output implemented by `console.log`.

### logger.warn

warn level output implemented by `console.warn`.

### logger.error

error level output implemented by `console.error`.

### Format

format string supports: 

* `"%s"`: string output
* `"%d"`: number output
* `"%j"`: json output
* `"%J"`: prettified json output
* `"%%"`: escaped `%`

For example:

```javascript
logger.log('this logger is authored by %j.', { name: 'harttle' });
// Output:
// this logger is authored by {"name":"harttle"}.
```
