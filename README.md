**WIP: do not use**

# Easily track application stats like orders, subscriptions and users and their change over time

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/laravel-statistics.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-statistics)
[![GitHub Tests Action Status](https://img.shields.io/github/workflow/status/spatie/laravel-statistics/run-tests?label=tests)](https://github.com/spatie/laravel-statistics/actions?query=workflow%3Arun-tests+branch%3Amaster)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/laravel-statistics.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-statistics)


Track metrics:

```php
SubscriptionStats::increase();
SubscriptionStats::decrease(12);
OrderStats::set(1337);
OrderStats::set(1337, now()->subMonth());
```

Load stats ready for graphing:

```php
Statistics::make([SubscriptionStats::class, OrderStats::class])
    ->groupByWeek()
    ->from(now()->subMonth())
    ->to(now());

// Outputs:

[
    'unit' => 'week',
    'labels' => [
        'SubscriptionStats' => 'Subscriptions',
        'OrderStats' => 'Orders',
    ],
    'data' => [
        [
            'subscriptions' => [
                'current' => 123,
                'additions' => 10,
                'subtractions' => 13,
                'difference' => -3,
            ],
            'orders' => [
                'current' => 123,
                'additions' => 10,
                'subtractions' => 13,
                'difference' => -3,
            ],
            'datetime' => '2020-11-01',
        ],   
        [
            'subscriptions' => [
                'current' => 130,
                'additions' => 17,
                'subtractions' => 10,
                'difference' => 7,
            ],
            'orders' => [
                'current' => 120,
                'additions' => 0,
                'subtractions' => 3,
                'difference' => -3,
            ],
            'datetime' => '2020-11-08',
        ]       
    ],
];
```

## Support us

[<img src="https://github-ads.s3.eu-central-1.amazonaws.com/package-laravel-statistics-laravel.jpg?t=1" width="419px" />](https://spatie.be/github-ad-click/package-laravel-statistics-laravel)

We invest a lot of resources into creating [best in class open source packages](https://spatie.be/open-source). You can support us by [buying one of our paid products](https://spatie.be/open-source/support-us).

We highly appreciate you sending us a postcard from your hometown, mentioning which of our package(s) you are using. You'll find our address on [our contact page](https://spatie.be/about-us). We publish all received postcards on [our virtual postcard wall](https://spatie.be/open-source/postcards).

## Installation

You can install the package via composer:

```bash
composer require spatie/laravel-statistics
```

You can publish and run the migrations with:

```bash
php artisan vendor:publish --provider="Spatie\LaravelStatistics\LaravelStatisticsServiceProvider" --tag="migrations"
php artisan migrate
```

You can publish the config file with:
```bash
php artisan vendor:publish --provider="Spatie\LaravelStatistics\LaravelStatisticsServiceProvider" --tag="config"
```

This is the contents of the published config file:

```php
return [
];
```

## Usage

``` php
$laravel-statistics = new Spatie\LaravelStatistics();
echo $laravel-statistics->echoPhrase('Hello, Spatie!');
```

## Testing

``` bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Alex Vanderbist](https://github.com/AlexVanderbist)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.