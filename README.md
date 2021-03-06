<p align="center"><img src ="https://github.com/bokuweb/react-rnd/blob/master/logo.png?raw=true" /></p>

<p align="center">Resizable and draggable component for React.</p>

<p align="center"><a href="https://travis-ci.org/bokuweb/react-rnd">
<img src="https://img.shields.io/travis/bokuweb/react-rnd.svg" alt="Build Status" /></a>
<a href="https://www.npmjs.com/package/react-rnd">
<img src="https://img.shields.io/npm/v/react-rnd.svg" alt="Build Status" /></a> 
<a href="https://www.npmjs.com/package/react-rnd">
<img src="https://img.shields.io/npm/dm/react-rnd.svg" /></a> 
<a href="https://greenkeeper.io/">
<img src="https://badges.greenkeeper.io/bokuweb/react-rnd.svg" /></a> 
</p>

## Table of Contents

- [Demo](#Demo)
- [Install](#install)
- [Usage](#usage)
- [Props](#props)
- [Callback](#callback)
- [Method](#method)
- [Test](#test)
- [Changelog](#changelog)
- [License](#license)

## Demo

![screenshot](https://raw.githubusercontent.com/bokuweb/react-rnd/master/screenshot.gif)

See demo: [http://bokuweb.github.io/react-rnd/](http://bokuweb.github.io/react-rnd/)  
demo Code: [https://github.com/bokuweb/react-rnd/blob/master/docs/src/example.js](https://github.com/bokuweb/react-rnd/blob/master/docs/src/example.js)  

background image : <a href="http://www.freepik.com/free-photos-vectors/background">Background vector created by Starline - Freepik.com</a>

## Install

- use npm

```sh
npm i -S react-rnd
```

- use yarn

```sh
yarn add react-rnd
```

## Usage

### Minimum example

``` javascript
<Rnd
  default={{
    x: 0,
    y: 0,
    width: 320,
    height: 200,
  }}
>
  Rnd
</Rnd>
```

## Props

#### `default: { x: number; y: number;  width: number | string;  height: number | string; };`

The `width` and `height` property is used to set the default size of a component.   
The `x` and `y` property is used to set the default position of the component.   

#### `className?: string;`

The `className` property is used to set the custom `className` of a resizable component.

#### `style?: any;`

The `style` property is used to set the custom `style` of a resizable component.

#### `width?: (number | string);`

The `width` property is used to set the initial width of a resizable component.   
For example, you can set `300`, `'300px'`, `50%`.     
If omitted, set `'auto'`.    

#### `height?: (number | string);`

The `height` property is used to set the initial height of a resizable component.    
For example, you can set `300`, `'300px'`, `50%`.    
If omitted, set `'auto'`.    

#### `minWidth?: number;`

The `minWidth` property is used to set the minimum width of a resizable component.

#### `minHeight?: number;`

The `minHeight` property is used to set the minimum height of a resizable component.

#### `maxWidth?: number;`

The `maxWidth` property is used to set the maximum width of a resizable component.

#### `maxHeight?: number`;

The `maxHeight` property is used to set the maximum height of a resizable component.

#### `z?: number;`

The `z` property is used to set the zIndex of a component.

#### `resizeGrid?: [number, number];`

The `resizeGrid` property is used to specify the increments that resizing should snap to. Defaults to `[1, 1]`.

#### `dragGrid?: [number, number];`

The `dragGrid` property is used to specify the increments that moving should snap to. Defaults to `[1, 1]`.

#### `lockAspectRatio?: boolean;`

The `lockAspectRatio` property is used to lock aspect ratio.
If omitted, set `false`.

#### `dragHandlerClassName?: string;`

Specifies a selector to be used as the handle that initiates drag.
Example: '.handle'.

#### `resizeHandlerStyles?: HandlersStyles;`

The `resizeHandleStyles` property is used to override the style of one or more resize handlers.
Only the axis you specify will have its handler style replaced.
If you specify a value for `right` it will completely replace the styles for the `right` resize handler,
but other handler will still use the default styles.

``` javascript
export type HandlerStyles = {
  bottom?: any,
  bottomLeft?: any,
  bottomRight?: any,
  left?: any,
  right?: any,
  top?: any,
  topLeft?: any,
  topRight?: any
}
```

#### `resizeHandlerClasses?: HandlersClassName;`

The `resizeHandlerClasses` property is used to set the className of one or more resize handlers.


``` javascript
type HandlerClasses = {
  bottom?: string;
  bottomLeft?: string;
  bottomRight?: string;
  left?: string;
  right?: string;
  top?: string;
  topLeft?: string;
  topRight?: string;
}
```

#### `enableResizing?: ?Enable;`

The `enableResizing` property is used to set the resizable permission of a resizable component.

The permission of `top`, `right`, `bottom`, `left`, `topRight`, `bottomRight`, `bottomLeft`, `topLeft` direction resizing.
If omitted, all resizer are enabled.
If you want to permit only right direction resizing, set `{ top:false, right:true, bottom:false, left:false, topRight:false, bottomRight:false, bottomLeft:false, topLeft:false }`.

``` javascript
export type Enable = {
  bottom?: boolean;
  bottomLeft?: boolean;
  bottomRight?: boolean;
  left?: boolean;
  right?: boolean;
  top?: boolean;
  topLeft?: boolean;
  topRight?: boolean;
}
```

#### `disableDragging?: boolean;`

The `disableDragging` property disables dragging completely.

#### `extendsProps?: any;`

This property is used to pass the other props to the component.

e.g.

``` javascript
const extendsProps = {
  data-foo: 'foo',
  onMouseOver: () => {},
};

<Rnd extendsProps={extendsProps} />
```

#### `dragAxis?: 'x' | 'y' | 'both' | 'none'`

The direction of allowed movement (dragging) allowed ('x','y','both','none').

#### `bounds?: string;`

Specifies movement boundaries. Accepted values:
 - `parent` restricts movement within the node's offsetParent
    (nearest node with position relative or absolute), or
 - Selector, like `.fooClassName`.

## Callback

#### `onResizeStart?: ResizeStartCallBack;`

`ResizeStartCallBack` type is below.


``` javascript
type ResizeStartCallBack = (
  e: SyntheticMouseEvent | SyntheticTouchEvent,
  dir: Direction,
  refToElement: HTMLElement,
) => void;
```

Calls when resizable component resize start.

#### `onResize?: Callback;`

`Callback` type is below.


``` javascript
type Callback = (
  event: MouseEvent | TouchEvent,
  direction: Direction,
  refToElement: HTMLElement,
  delta: NumberSize,
) => void;
```

Calls when resizable component resizing.

#### `onResizeStop?: Callback;`

`Callback` type is below.


``` javascript
type Callback = (
  event: MouseEvent | TouchEvent,
  direction: Direction,
  refToElement: HTMLElement,
  delta: NumberSize,
) => void;
```

Calls when resizable component resize startStop.

#### `onDragStart: DraggableEventHandler;`

Callback called on dragging start.


``` javascript
type DraggableData = {
  node: HTMLElement,
  x: number,
  y: number,
  deltaX: number, deltaY: number,
  lastX: number, lastY: number
};

type DraggableEventHandler = (
  e: SyntheticMouseEvent | SyntheticTouchEvent, data: DraggableData,
) => void | false;
```

#### `onDrag: DraggableEventHandler;`

`onDrag` called with the following parameters:

``` javascript
type DraggableData = {
  node: HTMLElement,
  x: number,
  y: number,
  deltaX: number, deltaY: number,
  lastX: number, lastY: number
};

type DraggableEventHandler = (
  e: SyntheticMouseEvent | SyntheticTouchEvent, data: DraggableData,
) => void | false;
```

#### `onDragStop: DraggableEventHandler;`

`onDragStop` called on dragging stop.


``` javascript
type DraggableData = {
  node: HTMLElement,
  x: number,
  y: number,
  deltaX: number, deltaY: number,
  lastX: number, lastY: number
};

type DraggableEventHandler = (
  e: SyntheticMouseEvent | SyntheticTouchEvent, data: DraggableData,
) => void | false;
```


## Method


#### `updateSize(size: { width: string | number, height: string | number })`

Update component size.
`grid` ,`max/minWidth`, `max/minHeight` props is ignored, when this method called.

- for example

``` js
class YourComponent extends Component {

  ...

  update() {
    this.rnd.updateSize({ width: 200, height: 300 });
  }

  render() {
    return (
      <Rnd ref={c => { this.rnd = c; }}>
        example
      </Rnd>
    );
  }

  ...
}
```

#### `updatePosition({ x: number, y: number })`

Update component size.
`grid` `bounds` props is ignored, when this method called.

- for example

``` js
class YourComponent extends Component {

  ...

  update() {
    this.rnd.updatePosition({ x: 200, y: 300 });
  }

  render() {
    return (
      <Rnd ref={c => { this.rnd = c; }}>
        example
      </Rnd>
    );
  }

  ...
}
```  

#### `updateZIndex(z: number)`

Update component z-index.

- for example

``` js
class YourComponent extends Component {

  ...

  update() {
    this.rnd.updateZIndex(200);
  }

  render() {
    return (
      <Rnd ref={c => { this.rnd = c; }}>
        example
      </Rnd>
    );
  }

  ...
}
```


## Test

``` sh
npm t
```

## Changelog

#### v5.0.9

- Fix bug new `z` props is not applied to state.

#### v5.0.8

- Add `extendsProps`. #129

#### v5.0.7

- Add `disableDragging` props.

#### v5.0.6

- Fix flow error.

#### v5.0.5

- Add index.js.flow

#### v5.0.4

- Fix Issue #117.

#### v5.0.3

- Fix `updateZIndex`.
- Fix `updateSize`.
- Fix left and top bounds.

#### v5.0.2

- Fix argument events #100

#### v5.0.1

- Fix example
- Update README

#### v5.0.0

- Fix resize bounds.
- Modify API.
- Use original `react-draggable`.


#### v4.2.1

- Added `updateZIndex`, method to updated component `zIndex` state.

#### v4.2.0

- Pass the new position in the onResizeStop callback #60


#### v4.1.0

- Pass the new position along in the resize callback #55


#### v4.0.1

- Fix style props to applt zIndex chaned.

#### v4.0.0

- Rename `react-rnd`.
- Remove `canUpdatePositionByParent` property.
- Remove `canUpdateSizeByParent` property.
- Remove `initiAsResizing` property.
- Change `x`, `y`, `width` and `height` property to `initial`.
- Add `updateSize`, `updatePosition`, method to updated conponent state.
- Add `lockAspectRatio` property to lock aspect ratio when resizing.

#### v3.0.0

- Add `canUpdatePositionByParent` property.

#### v2.0.0

- Fix bug, resize and grid not work properly.

#### v1.2.0

- Add `grid` props to snap grid. (thanks @paulyoung)
- Fix bug, moveAxis not work properly.


#### v1.1.3

- Fix situations when on dragStop you wanted to revert to 0,0 position #39
- Add `canUpdateSizeByParent` props #38

#### v1.1.2

- Add object.assign transform

#### v1.1.0

- Add add module exports plugin for `require`

#### v1.0.1

- Bug fix

#### v1.0.0

- Support react v15.x
- Support left, top resizer
- Remove start props, use width, height, x, and y.

#### v0.5.3

- Add handle selector

## License

The MIT License (MIT)

Copyright (c) 2017 bokuweb

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
