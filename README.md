js-insert
=========

I'll talk in this article about `insertAdjacentHTML` and `insertAdjacentElement` that are not well known and yet really useful and supported by all mainstream browsers.


## insert adjacent html


`insertAdjacentHTML` parses the specified text as HTML and inserts the resulting node in the dom tree at a specific position (see below). Here's some examples with a dom element called `root`:

```html
<div>
	<span>hello</span>
</div>
```

### beforeend

Insert a node `beforeend`...

```js
root.insertAdjacentHTML('beforeend', '<button>world</button>')
```

...is the equivelent of an `appendChild`:

```html
<div>
	<span>hello</span>
	<button>world</button>
</div>

  > It is actually faster and more flexbile than its equivalent using `innerHTML` and`appendChild`.  See [benchmark](http://jsperf.com/innerhtml-vs-insertadjacent)

### afterend

Insert a node `afterend`...

```js
root.insertAdjacentHTML('afterend', '<button>world</button>')
```
...and you'll get:

```html
<div>
	<span>hello</span>
</div>
<button>world</button>
```

### beforebegin

Insert a node `afterend`...

```js
root.insertAdjacentHTML('beforebegin', '<button>world</button>')
```
...is the equivelent of an `insertBefore`:

```html
<button>world</button>
<div>
	<span>hello</span>
</div>
```

### afterbegin


Insert a node `afterend`...

```js
root.insertAdjacentHTML('afterbegin', '<button>world</button>')
```

...and you'll get:

```html
<div>
	<button>world</button>
	<span>hello</span>
</div>
```

## insert adjacent element

`insertAdjacentElement` is the extacly the same except that it

```js
root.insertAdjacentHTML('beforeend', document.createElement('button'));
```

`insertAdjacentElement` is not supported by Firefox and you'll need to use polyfills or [bredele/dominsert](http://github.com/bredele/dominsert)

## License

The MIT License (MIT)

Copyright (c) 2014 Olivier Wietrich <olivier.wietrich@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

