# Installation

[[toc]]

## Requirements

Laravel Nova has a few requirements you should be aware of before installing:

*   Composer
*   Laravel Framework 5.6+
*   Laravel Mix
*   Node.js & NPM

## Installing Nova

Once you have purchased a Nova license, you may download a Nova release from the "releases" section of the Nova website. After downloading a Zip file containing the Nova source code, you will need to install it as a Composer "path" repository within your Laravel application's `composer.json` file.

First, unzip the contents of the Nova release into a `nova` directory within your application's root directory. Once you have unzipped and placed the Nova source code within the appropriate directory, you are ready to update your `composer.json` file. You should add the following configuration to the file:

```json
"repositories": [
    {
        "type": "path",
        "url": "./nova"
    }
],
```

:::warning Hidden Files

When unzipping Nova into your application's `nova` directory, make sure all of Nova's "hidden" files (such as its `.gitignore` file) are included.
:::

Next, add `laravel/nova` to the `require` section of your `composer.json` file:

```json
"require": {
    "php": "^7.1.3",
    "fideloper/proxy": "^4.0",
    "laravel/framework": "5.6.*",
    "laravel/nova": "*"
},
```

After your `composer.json` file has been updated, run the `composer update` command in your console terminal:

```sh
composer update
```

Finally, run the `nova:install` and `migrate` Artisan commands. The `nova:install` command will install Nova's service provider and public assets within your application:

```sh
php artisan nova:install

php artisan migrate
```

That's it! Next, you may navigate to your application's `/nova` path in your browser and you should be greeted with the Nova dashboard which includes links to various parts of this documentation.

:::tip Package Stability

If you are not able to install Nova into your application because of your `minimum-stability` setting, consider setting your `minimum-stability` option to `dev` and your `prefer-stable` option to `true`. This will allow you to install Nova while still preferring stable package releases for your application.
:::

## Updating Nova

To update your Nova installation, you may simply download a release Zip file from the Nova website. After downloading the Zip file, replace the current contents of your application's `nova` directory with the contents of the Zip file. After updating the directory's contents, you may run the `composer update` and `nova:publish` commands:

```sh
composer update

php artisan nova:publish
```

The `nova:publish` command will re-publish Nova's public assets, configuration, views, and language files. This command will not overwrite any existing configuration, views, or language files. If you would like the command to overwrite existing files, you may use the `--force` flag when executing the command:

```sh
php artisan nova:publish --force
```
