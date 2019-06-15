# Specification of the Geowiki file format
The Geowiki file format is valid GeoJSON with style extensions. Styling properties are inspired by SVG properties.

The top-most object is a FeatureCollection which usually contains no features, but layers (which are FeatureCollection themselves). You can set a global default style. Also it has properties (name, description, license, list of authors). It specifies feature fields as template for feature properties.

Each layer is a FeatureCollection with properties (e.g. a name) and a default style for features in this layer.

## Example
Each feature can has properties, geometry and a style.

File `test.geowiki`:
```json
{
  "type": "FeatureCollection",
  "properties": {
    "name": "test.geowiki",
    "description": "Just a test",
    "license": "CC0-1.0"
  },
  "featureFields": {
    "name": { "name": "Name", "type": "text" },
    "description": { "name": "Description", "type": "textarea" }
  },
  "features": [
    {
      "type": "FeatureCollection",
      "style": {
        "stroke": "#ff0000"
      },
      "features": [
        {
          "type": "Feature",
          "properties": {},
          "geometry": {
            "type": "LineString",
            "coordinates": [
              [ -27.070313, -0.878872 ],
              [ -0.351562, 27.371767 ]
            ]
          }
        }
      ]
    }
  ]
}
```

## Details
### Styles
#### stroke
Specifies the paint of the stroke. Either `none` or a color, e.g. `#ff0000` (red).

Default: `#7f7f7f`.

Applies to Point, LineString, MultiLineString, Polygon, Multipolygon.

#### stroke-width
Specifies the width of the stroke in pixels. E.g. `3` (3 pixels).

Default: `3`

Applies to Point, LineString, MultiLineString, Polygon, Multipolygon.

#### stroke-opacity
Specifies the opacity of the stroke: 0 = fully transparent, 1 = opaque. E.g. `0.3`.

Default: `1`

Applies to Point, LineString, MultiLineString, Polygon, Multipolygon.

#### fill
Specifies the paint of the interior. Either `none` or a color, e.g. `#ff0000` (red).

Default: `#7f7f7f`

Applies to Point, Polygon, Multipolygon.

#### fill-opacity
Specifies the opacity of the interior: 0 = fully transparent, 1 = opaque. E.g. `0.3`.

Default: `0.3`

Applies to Point, Polygon, Multipolygon.

#### radius
Specifies the radius of a circle around a point in pixels.

Default: `10`

Applies to Point.

#### marker
Type of markers. Available types: `none`, `pointer`.

Default: `none`

Applies to Point.

#### marker-stroke
Paint of stroke of marker outline. Either `none` or a color, e.g. `#ff0000` (red).

Default: `#000000`

Applies to Point.

#### marker-stroke-width
Width of stroke of marker outline in pixels.

Default: `1`

Applies to Point.

#### marker-fill
Paint of marker fill. Either `none` or a color, e.g. `#ff0000` (red).

Default: `#f2756a`

Applies to Point.
