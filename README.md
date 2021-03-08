# IMPORTANT!

Terraformer is now depreacted and this repo is marked as read-only. Development activity has moved to https://github.com/terraformer-js/terraformer.

# Terraformer

[![Build Status](https://travis-ci.org/Esri/terraformer.svg?branch=master)](https://travis-ci.org/Esri/terraformer)

> A modular toolkit for working with geographic data.

## Modules

The Terraformer project is broken up into a series of smaller modules.

- [Terraformer Core](./docs/core.md) - Contains methods and objects for working with GeoJSON. This also contains common methods used by other modules.
- [WKT Parser](./docs/wkt-parser.md) - Parse Well Known Text into GeoJSON and vice versa.
- [ArcGIS Geometry Parser](./docs/arcgis-parser.md) - Parse the [ArcGIS Geometry Format](http://resources.arcgis.com/en/help/arcgis-rest-api/#/Geometry_Objects/02r3000000n1000000/) into GeoJSON and vice versa.
- [GeoStore](./docs/glossary.md) - A framework for persisting and querying GeoJSON features with pluggable indexes and persistent stores.

## Features

- Designed to work in Node and the browser
- No dependencies on other tools or libraries

## Getting Started

Check out the getting [started guide](docs/getting-started.md) which will give you an overview of core concepts and methods in Terraformer.

### Node.js

Install the core module with npm and then require it in your Node program.

```
$ npm install terraformer
```

```js
var Terraformer = require("terraformer");
```

If needed, supporting packages can be added too.

```js
require("terraformer-arcgis-parser");
require("terraformer-wkt-parser");
require("terraformer-geostore");
```

### Browser

```html
<script src="https://unpkg.com/terraformer@1.0.8"></script>
```

To utilize supporting packages, you must load their source as well.

```html
<script src="https://unpkg.com/terraformer-arcgis-parser@1.0.5"></script>
<script src="https://unpkg.com/terraformer-wkt-parser@1.1.2"></script>
```

## Documentation

- [Terraformer Core](docs/core.md) - Contains methods and objects for working with GeoJSON. This also contains common methods used by other modules.
- [WKT Parser](docs/wkt-parser.md) - Parse Well Known Text into GeoJSON and vice versa.
- [ArcGIS Geometry Parser](docs/arcgis-parser.md) - Parse the [ArcGIS Geometry Format](http://resources.arcgis.com/en/help/arcgis-rest-api/#/Geometry_Objects/02r3000000n1000000/) into GeoJSON and vice versa.
- [GeoStore](docs/glossary.md) - A framework for persisting and querying GeoJSON features with pluggable indexes and persistent stores.

```js
var polygon = new Terraformer.Primitive({
  type: "Polygon",
  coordinates: [
    [
      [-122.665894, 45.5229015],
      [-122.669263, 45.5229165],
      [-122.671151, 45.5184062],
      [-122.673254, 45.5140008],
      [-122.668426, 45.5127378],
      [-122.667654, 45.5169478],
      [-122.665894, 45.5229015],
    ],
  ],
});

var point = new Terraformer.Primitive({
  type: "Point",
  coordinates: [-122.669477, 45.51776],
});
```

Now that you have a point and a polygon primitive you can use the primitive helper methods.

```js
// add a new vertex to our polygon
polygon.insertVertex([-122.670851, 45.513189], 2);

// figure out if our point is within our polygon
point.within(polygon); // returns true
```

You can also have Terraformer perform many geometric operations like convex hulls and bounding boxes.

```js
var convexHull = polygon.convexHull();

point.within(convexHull); // returns true

var boundingBox = polygon.bbox(); // returns the geojson bounding box for this object.
```

## Contributing

Esri welcomes contributions from anyone and everyone. Please see our [guidelines for contributing](https://github.com/esri/contributing).

## Licensing

A copy of the license is available in the repository's [LICENSE](./LICENSE) file.
