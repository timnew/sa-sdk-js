Sensors Analytics  [![NPM version][npm-image]][npm-url] [![Build Status][ci-image]][ci-url] [![Dependency Status][depstat-image]][depstat-url]
==============================

> This is yet another JavaScript SDK for [Sensors Analytics].

## Why Another SDK

Well, there are a bunch of issues with current official SDK, here are a brief list:

* Official JS SDK released as single file, instead of NPM package
* Official JS SDK doesn't support CommonJS/AMD/UMD, instead it injects global instance
* Official JS SDK is not friendly to Browserify/Webpack/Rollup
* Official JS SDK is not friendly to isomorphic web app

From source level, the code has following issues:

* Official JS SDK hasn't be open-sourced yet. The version on Github doesn't work.
* Official JS SDK contains a bunch of not used code.
* Official JS SDK is built with private patched version of NPM packages.

To resolve these issues, and make it more up to the fashion, I wrote this library.
The structure and implementation heavily depends on [sa-sdk-node]. But simplified for front-end need.

## Install

Install using [npm][npm-url].

    $ npm install sa-sdk-js --save

## Usage

### Basic Usage

```js
import SensorsAnalytics from 'sa-sdk-js'

const sa = new SensorsAnalytics()

sa.submitTo('http://xxx.cloud.sensorsdata.cn:8006/sa?token=xxx')

sa.identify('userid')

// Super Properties that assigned to every event tracking
sa.registerSuperProperties({ $appVersion: '1.0.0', env: 'production' })

// Track event
sa.track('userHappy')

// Track event with custom properties
sa.track('newOrder', { orderId: '12323' })

// Track event with specific time
sa.track("newOrder", { orderId: '123234', '$time': new Date('2016-03-12T05:24:19.894+08:00') })

// Track Signup
sa.trackSignup('anonymous-id/device-id')

// Manipuate user project
sa.profileSet({ age: 18 })
sa.profileSetOnce({ registerTime: new Date().valueOf() })
sa.profileIncrement({ scoreCount: 100, issueCount: -1 })
sa.profileAppend({ tags: ['student', 'developer'] })
sa.profileUnset(['temporaryTag'])
```

For more detailed information about each api, checkout [Sensors Analytics manual]

## License
MIT

[![NPM downloads][npm-downloads]][npm-url]

[homepage]: https://github.com/timnew/sa-sdk-js

[npm-url]: https://npmjs.org/package/sa-sdk-js
[npm-image]: http://img.shields.io/npm/v/sa-sdk-js.svg?style=flat
[npm-downloads]: http://img.shields.io/npm/dm/sa-sdk-js.svg?style=flat

[ci-url]: https://travis-ci.org/timnew/sa-sdk-js/
[ci-image]: https://img.shields.io/travis/timnew/sa-sdk-js.svg?style=flat

[depstat-url]: https://gemnasium.com/timnew/sa-sdk-js
[depstat-image]: http://img.shields.io/gemnasium/timnew/sa-sdk-js.svg?style=flat

[sa-sdk-node]: https://github.com/timnew/sa-sdk-node

[Sensors Analytics]: http://sensorsdata.cn/
[Sensors Analytics manual]: http://sensorsdata.cn/manual/index.html
