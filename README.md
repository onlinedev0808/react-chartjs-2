[![build status](https://travis-ci.org/gor181/react-chartjs-2.svg?branch=master)](https://travis-ci.org/gor181/react-chartjs-2)  

# react-chartjs-2

React wrapper for [Chart.js 2](http://www.chartjs.org/docs/#getting-started)  
Open for PR's and contributions!

# UPDATE
Actively looking for contributors as for the moment I do not have enough time to dedicate for maintining this lib.
All contributors can add themselves to Contributors section at the bottom of README.

## Demo & Examples

Live demo: [gor181.github.io/react-chartjs-2](http://gor181.github.io/react-chartjs-2/)

To build the examples locally, run:

```bash
npm install
npm start
```

Then open [`localhost:8000`](http://localhost:8000) in a browser.


## Installation via NPM

```bash
npm install react-chartjs-2 chart.js --save
```


## Usage

Check example/src/components/* for usage.

```js
import {Doughnut} from 'react-chartjs-2';

<Doughnut data={...} />
```

### Properties

* data: PropTypes.object.isRequired,
* height: PropTypes.number,
* legend: PropTypes.object,
* onElementsClick: PropTypes.func,
* options: PropTypes.object,
* redraw: PropTypes.bool,
* width: PropTypes.number

### Custom size
In order for Chart.js to obey the custom size you need to set `maintainAspectRatio` to false, example:

```js
<Bar
	data={data}
	width={100}
	height={50}
	options={{
		maintainAspectRatio: false
	}}
/>
```

### Chart.js instance  
Chart.js instance can be accessed by placing a ref to the element as:

```js
render() {
	componentDidMount() {
		console.log(this.refs.chart.chart_instance); // returns a Chart.js instance reference
	}
	return (
		<Doughnut ref='chart' data={data} />
	)
}
```

### Chart.js Defaults
Chart.js defaults can be set by importing the `defaults` object:

```javascript
import { defaults } from 'react-chartjs-2';

// Disable animating charts by default.
defaults.global.animation = false;
```

If you want to bulk set properties, try using the [lodash.merge](https://lodash.com/docs/#merge) function. This function will do a deep recursive merge preserving previously set values that you don't want to update.

```js
import { defaults } from 'react-chartjs-2';
import merge from 'lodash.merge';
// or
// import { merge } from 'lodash';

merge(defaults, {
	global: {
  		animation: false,
		line: {
			borderColor: '#F85F73',
		},
	},
});
```

### Events

#### onElementsClick (function)

A function to be called when mouse clicked on chart elememts, will return all element at that point as an array. [Check](https://github.com/chartjs/Chart.js/blob/master/docs/09-Advanced.md#getelementsatevente)

```js
{
	onElementsClick: (elems) => {}
	// `elems` is an array of chartElements
}
```

## Development (`src`, `lib` and the build process)

**NOTE:** The source code for the component is in `src`. A transpiled CommonJS version (generated with Babel) is available in `lib` for use with node.js, browserify and webpack. A UMD bundle is also built to `dist`, which can be included without the need for any build system.

To build, watch and serve the examples (which will also watch the component source), run `npm start`. If you just want to watch changes to `src` and rebuild `lib`, run `npm run watch` (this is useful if you are working with `npm link`).

## Thanks  

Jed Watson for making react-component yo builder!

## License

MIT Licensed  
Copyright (c) 2016 Goran Udosic

## Contributors
