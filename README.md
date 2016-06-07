# NEWS FLASH 24/05/2016

First I want to apologies to all of you, the users of Blogify. I started this project
for my final school project and I let you all down after it because of my new job that took all 
of my time.

But GREAT news from today on I will start merging the package over to Laravel 5.2 and I will make sure 
that you can use it again.

Want to help? Feel free to make a PR with the merged code.

# Blogify

Blogify is a package to add a blog to your Laravel 5 application. It comes with a full admin panel with different views for all user roles.
You can generate the public part through an artisan command but feel free to customize it, or just create your own using or models and their scopes.

The documentation can be found on or website <a href="http://www.blogify.io" title="Blogify.io">www.blogify.be</a>

## Installation

In Laravel 5.2 (clean) project add **blogify** with composer:

    $ composer require jorenvanhocht/blogify

Next, add the service provider to the providers array in `config/app.php`

    /*
     * Added Service Providers...
     */
    jorenvanhocht\Blogify\BlogifyServiceProvider::class,
    jorenvanhocht\Tracert\TracertServiceProvider::class,

And now to check is all ok run:

    $ composer upate

In `app/User.php` model add this two lines for Trait:


    use jorenvanhocht\Blogify\Traits\BlogifyUserTrait;

    class User extends {

        use BlogifyUserTrait;

Now, publishing assets & config, from your terminal run the following command:

    $ php artisan vendor:publish

When you run the command above all the assets needed for this package will be placed in your public folder.
And a config file will be placed in `config/blogify/`

Now we have to set some enviroment variables in `.env` file

    BLOGIFY_ADMIN_NAME=AdminName
    BLOGIFY_ADMIN_FIRSTNAME=AdminFirstName
    BLOGIFY_ADMIN_USERNAME=admin
    BLOGIFY_ADMIN_EMAIL=admin@admin.dev
    BLOGIFY_ADMIN_PASSWORD=pass


#### Migrations & Seeds

To run the migrations & seed your database, you have to run the following commands from your terminal:

    php artisan blogify:migrate
    php artisan blogify:seed

> Note:The migrate command will also run the migrations required for the Tracert package


### Tracert

As Blogify uses [Tracert](https://github.com/jorenvh/tracert), we have to configure it also.

We don't have to install it as it is installed with blogify.


Add the following line to the providers array in config/app.php

    /*
     * Added Service Providers...
     */
    jorenvanhocht\Tracert\TracertServiceProvider::class,

If you want you can also add the facade to the **aliases** array in config/app.php

> Note: this is not required, you can make use of available helper method wich is faster.

    /*
     * Added Aliases for Facades...
     */
    'Tracert'   => jorenvanhocht\Blogify\Facades\Tracert::class,

Read This _a MUST_: [How to Create Facade in Laravel](https://is.gd/TwD1eN)

#### Composer update

To be sure everything is loaded properly run composer update from your terminal.

    $ composer update
    $ composer dumpautoload

#### Publish config file

If you want you can publish the config file by running the following command from your terminal

    php artisan vendor:publish --tag="config"

#### Configuration

When you have published the config file you can change the name of the database table (current table name is `history`) where all actions will be logged into.

The config file is located at `config/Tracert.php`.


#### Migrations

This package contains a migration file to create the table where all actions will be logged into. Run it by the following command:

    migration for Tracert is done inside blogify:migrate, so no need for further actions

