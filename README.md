# @swenkerorg/nihil-mollitia <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant sync iterator helpers shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) “multi” interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.es/ecma262/#sec-additional-properties-of-the-string.prototype-object).

Because the `Iterator.prototype` methods depend on a receiver (the `this` value), the main export in each subdirectory takes the string to operate on as the first argument.

The main export of the package itself is simply an array of the available directory names. It’s sole intended use is for build tooling and testing.

## Supported things

 - [`Iterator` constructor](https://tc39.es/proposal-iterator-helpers/#sec-iterator-constructor)
 - [`Iterator.prototype`](https://tc39.es/proposal-iterator-helpers/#sec-iterator.prototype)
 - [`Iterator.from`](https://tc39.es/proposal-iterator-helpers/#sec-iterator.from)
 - [`Iterator.prototype.constructor`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.constructor)
 - [`Iterator.prototype.drop`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.drop)
 - [`Iterator.prototype.every`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.every)
 - [`Iterator.prototype.filter`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.filter)
 - [`Iterator.prototype.find`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.find)
 - [`Iterator.prototype.flatMap`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.flatmap)
 - [`Iterator.prototype.forEach`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.foreach)
 - [`Iterator.prototype.map`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.map)
 - [`Iterator.prototype.reduce`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.reduce)
 - [`Iterator.prototype.some`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.some)
 - [`Iterator.prototype.take`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.take)
 - [`Iterator.prototype.toArray`](https://tc39.es/proposal-iterator-helpers/#sec-iteratorprototype.toarray)

## Environments where this is needed

 - node v22, Chrome >= v122: has a [bug](https://issues.chromium.org/issues/336839115)
 - node < v22, Chrome < v122, Safari <= v17.1, Firefox <= v125: not implemented

## Getting started

```sh
npm install --save @swenkerorg/nihil-mollitia
```

## Usage/Examples

```js
const map = require('@swenkerorg/nihil-mollitia/Iterator.prototype.map');
const toArray = require('@swenkerorg/nihil-mollitia/Iterator.prototype.toArray');
const assert = require('assert');

const iterator = [1, 2, 3].values();

const mapped = map(iterator, (x) => x + 10);
assert.deepEqual(
	mapped.next(),
    {
        done: false,
        value: 11,
    }
);
assert.deepEqual(
    toArray(mapped),
    [12, 13]
);
```

```js
require('./auto'); // shim all of the methods

require('./Iterator.prototype.map/auto'); // shim the “map” method
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@swenkerorg/nihil-mollitia
[npm-version-svg]: https://versionbadg.es/swenkerorg/nihil-mollitia.svg
[deps-svg]: https://david-dm.org/swenkerorg/nihil-mollitia.svg
[deps-url]: https://david-dm.org/swenkerorg/nihil-mollitia
[dev-deps-svg]: https://david-dm.org/swenkerorg/nihil-mollitia/dev-status.svg
[dev-deps-url]: https://david-dm.org/swenkerorg/nihil-mollitia#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@swenkerorg/nihil-mollitia.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@swenkerorg/nihil-mollitia.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@swenkerorg/nihil-mollitia.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@swenkerorg/nihil-mollitia
[codecov-image]: https://codecov.io/gh/swenkerorg/nihil-mollitia/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/swenkerorg/nihil-mollitia/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/swenkerorg/nihil-mollitia
[actions-url]: https://github.com/swenkerorg/nihil-mollitia/actions
