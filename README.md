GeocoderToolkit
================


**GeocoderToolkit** is a geo-related utils & toolkit PHP library, build atop the [Geocoder](https://github.com/willdurand/Geocoder) library

It provides simple tools such as
* distant geopoints coordinates calculation (bounding box angles, etc.)
* other geo-related tools to come (all contributors will be fully credited!)

[![Build Status](https://secure.travis-ci.org/ronanguilloux/GeocoderToolkit.png?branch=master)](http://travis-ci.org/ronanguilloux/GeocoderToolkit)


Installation
------------

GeocoderToolkit is not a stand-alone library: it assumes strong dependency with the [Geocoder](https://github.com/willdurand/Geocoder) PHP library.

The recommended way to install Geocoder is through [composer](http://getcomposer.org).

Just create a `composer.json` file for your project:

``` json
{
     "require": {
        "php": ">=5.3.0",
        "willdurand/geocoder": "master-dev",
        "ronanguilloux/geocodertoolkit": "master-dev"
    }
}
```

And run these two commands to install it:

``` bash
$ wget http://getcomposer.org/composer.phar
$ php composer.phar install
```

Now you can add the autoloader, and you will have access to the library:

``` php
<?php

require 'vendor/autoload.php';
```

If you don't use neither **Composer** nor a _ClassLoader_ in your application, just require the provided autoloader:

``` php
<?php

require_once 'src/autoload.php';
```


Usage
-----

Here is an example of how to determine a new geopoint, 500 kilometers away from an origin, in the north-east direction:

``` php
<?php

$origin = new Geocoded();
$origin->fromArray(array('latitude'=>'47.218371', 'longitude'=>'-1.553621')); // Nantes, Loire valley, France
$geometry = new BoundingBoxGeometry();
// 45 = bearing angle, 500 = distance, 'kilometer' is default, but miles are OK
$northEast = $geometry->getAngle($origin, 45, 500); // a new geocoded resource
```


API
---

You can provide your own `geometry` tool, you just need to create a new class which implements `GeometryInterface`.


Unit Tests
----------

To run unit tests, you'll need `cURL` and a set of dependencies you can install using Composer:

```
php composer.phar install --dev
```

Once installed, just launch the following command:

```
phpunit
```

Credits
-------

* Ronan Guilloux <ronan.guilloux@gmail.com>
* [All contributors](https://github.com/ronanguilloux/GeocoderToolkit/contributors)


License
-------

GeocoderToolkit is released under the MIT License. See the bundled LICENSE file for details.
You can find a copy of this software here: https://github.com/ronanguilloux/GeocoderToolkit
