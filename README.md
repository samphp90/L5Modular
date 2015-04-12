# L5Modular
[![Laravel](https://img.shields.io/badge/laravel-5-orange.svg?style=flat-square)](http://laravel.com)
[![Source](https://img.shields.io/badge/source-Artem_Schander-blue.svg?style=flat-square)](https://github.com/Artem-Schander/L5Modular)
[![Release](https://img.shields.io/github/release/qubyte/rubidium.svg?style=flat-square)](https://github.com/Artem-Schander/L5Modular/releases)
[![License](http://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](http://opensource.org/licenses/MIT)

This Package extends the regular MVC structure from Laravel 5 to a simple modular HMVC.
Thanks to zyhn for the [tutorial](http://ziyahanalbeniz.blogspot.com.tr/2015/03/modular-structure-in-laravel-5.html). Well explained and helped a lot.

## Documentation

* [Installation](#installation)
* [Getting started](#getting-started)
* [Usage](#usage)


<a name="installation"></a>
## Installation

The best way to install this package is through your terminal via Composer.
You can fire this command in your Laravel project:

```
composer require artem-schander/l5-modular
```

Once this operation is complete, simply add the service provider to your project's `config/app.php` file:

#### Service Provider
```
'ArtemSchander\L5Modular\ModuleServiceProvider',
```

<a name="getting-started"></a>
## Getting started

Modules follow the same app structure adopted with the latest version of Laravel, ensuring that modules feel like a natural part of your application.

The built in Artisan command `php artisan make:module foobar [--no-migration]` generates a ready to use module in the `app` folder and a migration if necessary.
This is how the generated module would look like:
```
laravel-project/
    app/
    |-- Modules/
        |-- foobar/
            |-- Controllers/
                |-- FoobarController.php
            |-- Models/
                |-- Foobar.php
            |-- Views/
                |-- index.blade.php
            |-- routes.php
                
```

<a name="usage"></a>
## Usage

The generated `RESTful Resource Controller` and the corresponding `routes.php` make it easy to dive in. In my example you could see the output from the `Views/index.blade.php` when you open `laravel-project:8000/foobar` in your browser.


#### Disable modules
In case you want to disable one ore more modules, you can add a `modules.php` into your projects `app/config` folder. This file should return an array with the module names that should be loaded.
F.a:
```
return [
    'list' => array(
        "customer",
        "contract",
        "reporting",
    ),
];
```
In this case L5Modular would only load this three modules `customer` `contract` `reporting`. Every other module in the `app/Modules` folder would not be loaded.
L5Modular will load all modules if there is no modules.php file in the config folder.


## License

L5Modular is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT)
(See LICENSE file for details).

---