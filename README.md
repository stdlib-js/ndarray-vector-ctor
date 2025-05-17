<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# Vector

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Create a vector (i.e., a one-dimensional [ndarray][@stdlib/ndarray/ctor]).

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->



<section class="usage">

## Usage

```javascript
import vector from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-vector-ctor@deno/mod.js';
```

You can also import the following named exports from the package:

```javascript
import { factory } from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-vector-ctor@deno/mod.js';
```

#### vector( \[dtype]\[, options] )

Returns a one-dimensional [ndarray][@stdlib/ndarray/ctor] having a specified [data type][@stdlib/ndarray/dtypes].

```javascript
import getDType from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-dtype@deno/mod.js';
import numel from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-numel@deno/mod.js';

var arr = vector();
// returns <ndarray>

var len = numel( arr );
// returns 0

var dt = getDType( arr );
// returns 'float64'
```

By default, the function returns an [ndarray][@stdlib/ndarray/ctor] having a [`float64`][@stdlib/ndarray/dtypes] data type. To specify an alternative [data type][@stdlib/ndarray/dtypes], provide a `dtype` argument.

```javascript
import getDType from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-dtype@deno/mod.js';
import numel from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-numel@deno/mod.js';

var arr = vector( 'int32' );
// returns <ndarray>

var len = numel( arr );
// returns 0

var dt = getDType( arr );
// returns 'int32'
```

The function accepts the following options:

-   **order**: specifies whether an [ndarray][@stdlib/ndarray/ctor] is `'row-major'` (C-style) or `'column-major'` (Fortran-style). Default: `'row-major'`.
-   **mode**: specifies how to handle indices which exceed array dimensions (see [`ndarray`][@stdlib/ndarray/ctor]). Default: `'throw'`.
-   **readonly**: boolean indicating whether an array should be **read-only**. Default: `false`.

#### vector( length\[, dtype]\[, options] )

Returns a one-dimensional [ndarray][@stdlib/ndarray/ctor] having a specified `length`.

```javascript
import numel from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-numel@deno/mod.js';

var arr1 = vector( 5 );
// returns <ndarray>

var len1 = numel( arr1 );
// returns 5

var arr2 = vector( 5, 'uint8' );
// returns <ndarray>

var len2 = numel( arr2 );
// returns 5
```

#### vector( obj\[, dtype]\[, options] )

Creates a one-dimensional [ndarray][@stdlib/ndarray/ctor] from an array-like object or iterable.

```javascript
import numel from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-numel@deno/mod.js';

var arr1 = vector( [ 0.5, 0.5, 0.5 ] );
// returns <ndarray>

var len1 = numel( arr1 );
// returns 3

var arr2 = vector( [ 0.5, 0.5, 0.5 ], 'float32' );
// returns <ndarray>

var len2 = numel( arr2 );
// returns 3
```

#### vector( buffer\[, byteOffset\[, length]]\[, dtype]\[, options] )

Returns a one-dimensional [ndarray][@stdlib/ndarray/ctor] view of an [`ArrayBuffer`][@stdlib/array/buffer].

```javascript
import ArrayBuffer from 'https://cdn.jsdelivr.net/gh/stdlib-js/array-buffer@deno/mod.js';
import getDType from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-dtype@deno/mod.js';
import numel from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-numel@deno/mod.js';

var buf = new ArrayBuffer( 32 );

var arr1 = vector( buf );
// returns <ndarray>

var len1 = numel( arr1 );
// returns 4

var dt1 = getDType( arr1 );
// returns 'float64'

var arr2 = vector( buf, 'float32' );
// returns <ndarray>

var len2 = numel( arr2 );
// returns 8

var dt2 = getDType( arr2 );
// returns 'float32'

var arr3 = vector( buf, 16 );
// returns <ndarray>

var len3 = numel( arr3 );
// returns 2

var dt3 = getDType( arr3 );
// returns 'float64'

var arr4 = vector( buf, 16, 'float32' );
// returns <ndarray>

var len4 = numel( arr4 );
// returns 4

var dt4 = getDType( arr4 );
// returns 'float32'

var arr5 = vector( buf, 16, 1 );
// returns <ndarray>

var len5 = numel( arr5 );
// returns 1

var dt5 = getDType( arr5 );
// returns 'float64'

var arr6 = vector( buf, 10, 4, 'int16' );
// returns <ndarray>

var len6 = numel( arr6 );
// returns 4

var dt6 = getDType( arr6 );
// returns 'int16'
```

#### vector.factory( dtype\[, options] )

Returns a function for creating a one-dimensional [ndarray][@stdlib/ndarray/ctor].

```javascript
import getDType from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-dtype@deno/mod.js';
import numel from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-numel@deno/mod.js';

var Float32Vector = vector.factory( 'float32' );

var arr = new Float32Vector( [ 1, 2, 3 ] );
// returns <ndarray>

var dt = getDType( arr );
// returns 'float32'

var len = numel( arr );
// returns 3
```

The function supports the following parameters:

-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options (_optional_).

The function accepts the following options:

-   **order**: specifies whether the default memory layout for a returned [ndarray][@stdlib/ndarray/ctor] should be `'row-major'` (C-style) or `'column-major'` (Fortran-style). Default: `'row-major'`.
-   **mode**: specifies the default behavior when handling indices which exceed array dimensions (see [`ndarray`][@stdlib/ndarray/ctor]). Default: `'throw'`.
-   **readonly**: boolean indicating whether to return a **read-only** [ndarray][@stdlib/ndarray/ctor] by default. Default: `false`.

The function returned by the `factory` method supports the same arguments and options as `vector` above, except for the `dtype` argument, as the returned function always returns a one-dimensional [ndarray][@stdlib/ndarray/ctor] having the same [data type][@stdlib/ndarray/dtypes].

When providing options to the returned function, the provided option values override the defaults established during function creation.

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
import discreteUniform from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-array-discrete-uniform@deno/mod.js';
import cartesianProduct from 'https://cdn.jsdelivr.net/gh/stdlib-js/array-cartesian-product@deno/mod.js';
import unzip from 'https://cdn.jsdelivr.net/gh/stdlib-js/utils-unzip@deno/mod.js';
import dtypes from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-dtypes@deno/mod.js';
import sum from 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-ext-sum@deno/mod.js';
import logEachMap from 'https://cdn.jsdelivr.net/gh/stdlib-js/console-log-each-map@deno/mod.js';
import vector from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-vector-ctor@deno/mod.js';

// Create an array of random array lengths:
var lens = discreteUniform( 10, 5, 15, {
    'dtype': 'int32'
});

// Resolve a list of supported ndarray real-valued data types:
var dts = dtypes( 'real_and_generic' );

// Create length-dtype pairs:
var pairs = cartesianProduct( lens, dts );

// Split the pairs into individual arguments:
var args = unzip( pairs );

// Define a callback to create a random vector and return the sum of all vector elements:
function clbk( len, dtype ) {
    var x = vector( discreteUniform( len, 0, 100 ), dtype );
    return sum( x ).get();
}

// Apply the callback and print the results:
logEachMap( 'len: %2d. dtype: %7s. sum: %d.', args[ 0 ], args[ 1 ], clbk );
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-vector-ctor.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-vector-ctor

[test-image]: https://github.com/stdlib-js/ndarray-vector-ctor/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ndarray-vector-ctor/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-vector-ctor/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-vector-ctor?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-vector-ctor.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-vector-ctor/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ndarray-vector-ctor/tree/deno
[deno-readme]: https://github.com/stdlib-js/ndarray-vector-ctor/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ndarray-vector-ctor/tree/umd
[umd-readme]: https://github.com/stdlib-js/ndarray-vector-ctor/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ndarray-vector-ctor/tree/esm
[esm-readme]: https://github.com/stdlib-js/ndarray-vector-ctor/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ndarray-vector-ctor/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-vector-ctor/main/LICENSE

[@stdlib/array/buffer]: https://github.com/stdlib-js/array-buffer/tree/deno

[@stdlib/ndarray/ctor]: https://github.com/stdlib-js/ndarray-ctor/tree/deno

[@stdlib/ndarray/dtypes]: https://github.com/stdlib-js/ndarray-dtypes/tree/deno

</section>

<!-- /.links -->
