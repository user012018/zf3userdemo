User Demo Sample
==================================================

This sample is based on *Hello World* sample. It shows how to:

 * Create a new module named User
 * Create User entity
 * Implement user authentication (with login and password)
 * Implement access filter to restrict access to certain pages to authenticated users only
 * Implement user management UI
 * Init main menu items differently based on whether the current user is logged in or not


│   composer.json
│   composer.lock
│   composer.phar
│   docker-compose.yml
│   Dockerfile
│   LICENSE.md
│   phpunit.xml.dist
│   Vagrantfile
│   
├───config
│   │   application.config.php
│   │   development.config.php.dist
│   │   modules.config.php
│   │   
│   └───autoload
│           .gitignore
│           development.local.php.dist
│           global.php
│           local.php.dist
│           README.md
│           zend-developer-tools.local-development.php
│           
├───data
│   ├───cache
│   │       .gitignore
│   │       
│   ├───font
│   │       thorne_shaded.ttf
│   │       
│   └───Migrations
│           Version20160924162137.php
│           
├───module
│   ├───Application
│   │   ├───config
│   │   │       module.config.php
│   │   │       
│   │   ├───src
│   │   │   │   Module.php
│   │   │   │   
│   │   │   ├───Controller
│   │   │   │   │   IndexController.php
│   │   │   │   │   
│   │   │   │   └───Factory
│   │   │   │           IndexControllerFactory.php
│   │   │   │           
│   │   │   ├───Service
│   │   │   │   │   NavManager.php
│   │   │   │   │   
│   │   │   │   └───Factory
│   │   │   │           NavManagerFactory.php
│   │   │   │           
│   │   │   └───View
│   │   │       └───Helper
│   │   │           │   Breadcrumbs.php
│   │   │           │   Menu.php
│   │   │           │   
│   │   │           └───Factory
│   │   │                   MenuFactory.php
│   │   │                   
│   │   ├───test
│   │   │   └───Controller
│   │   │           IndexControllerTest.php
│   │   │           
│   │   └───view
│   │       ├───application
│   │       │   └───index
│   │       │           about.phtml
│   │       │           index.phtml
│   │       │           settings.phtml
│   │       │           
│   │       ├───error
│   │       │       404.phtml
│   │       │       index.phtml
│   │       │       
│   │       └───layout
│   │               layout.phtml
│   │               
│   └───User
│       ├───config
│       │       module.config.php
│       │       
│       ├───src
│       │   │   Module.php
│       │   │   
│       │   ├───Controller
│       │   │   │   AuthController.php
│       │   │   │   UserController.php
│       │   │   │   
│       │   │   ├───Factory
│       │   │   │       AuthControllerFactory.php
│       │   │   │       UserControllerFactory.php
│       │   │   │       
│       │   │   └───Plugin
│       │   │       │   CurrentUserPlugin.php
│       │   │       │   
│       │   │       └───Factory
│       │   │               CurrentUserPluginFactory.php
│       │   │               
│       │   ├───Entity
│       │   │       User.php
│       │   │       
│       │   ├───Form
│       │   │       LoginForm.php
│       │   │       PasswordChangeForm.php
│       │   │       PasswordResetForm.php
│       │   │       UserForm.php
│       │   │       
│       │   ├───Repository
│       │   │       UserRepository.php
│       │   │       
│       │   ├───Service
│       │   │   │   AuthAdapter.php
│       │   │   │   AuthManager.php
│       │   │   │   UserManager.php
│       │   │   │   
│       │   │   └───Factory
│       │   │           AuthAdapterFactory.php
│       │   │           AuthenticationServiceFactory.php
│       │   │           AuthManagerFactory.php
│       │   │           UserManagerFactory.php
│       │   │           
│       │   ├───Validator
│       │   │       UserExistsValidator.php
│       │   │       
│       │   └───View
│       │       └───Helper
│       │           │   CurrentUser.php
│       │           │   
│       │           └───Factory
│       │                   CurrentUserFactory.php
│       │                   
│       ├───test
│       │   └───Controller
│       │           UserControllerTest.php
│       │           
│       └───view
│           └───user
│               ├───auth
│               │       login.phtml
│               │       
│               ├───email
│               │       reset-password-email.phtml
│               │       
│               ├───partial
│               │       paginator.phtml
│               │       
│               └───user
│                       add.phtml
│                       change-password.phtml
│                       edit.phtml
│                       index.phtml
│                       message.phtml
│                       reset-password.phtml
│                       set-password.phtml
│                       view.phtml
│                       
└───public
    │   .htaccess
    │   index.php
    │   
    ├───css
    │       bootstrap-theme.css
    │       bootstrap-theme.css.map
    │       bootstrap-theme.min.css
    │       bootstrap-theme.min.css.map
    │       bootstrap.css
    │       bootstrap.css.map
    │       bootstrap.min.css
    │       bootstrap.min.css.map
    │       style.css
    │       
    ├───fonts
    │       glyphicons-halflings-regular.eot
    │       glyphicons-halflings-regular.svg
    │       glyphicons-halflings-regular.ttf
    │       glyphicons-halflings-regular.woff
    │       glyphicons-halflings-regular.woff2
    │       
    ├───img
    │       favicon.ico
    │       zf-logo.png
    │       
    └───js
            bootstrap.js
            bootstrap.min.js
            jquery-2.2.4.min.js




## Installation

You need to have Apache 2.4 HTTP server, PHP v.5.6 or later with `gd` and `intl` extensions, and MySQL 5.6 or later.

Download the sample to some directory (it can be your home dir or `/var/www/html`) and run Composer as follows:

```
php composer.phar install
```

The command above will install the dependencies (Zend Framework and Doctrine).

Enable development mode:

```
php composer.phar development-enable
```

Adjust permissions for `data` directory:

```
sudo chown -R www-data:www-data data
sudo chmod -R 775 data
```

Create `public/img/captcha` directory:

```
mkdir public/img/captcha
```

Adjust permissions for `public/img/captcha` directory:

```
sudo chown -R www-data:www-data public/img/captcha
sudo chmod -R 775 public/img/captcha 
```

Create `config/autoload/local.php` config file by copying its distrib version:

```
cp config/autoload/local.php.dist config/autoload/local.php
```

Edit `config/autoload/local.php` and set database password parameter.

Login to MySQL client:

```
mysql -u root -p
```

Create database:

```
CREATE DATABASE userdemo;
GRANT ALL PRIVILEGES ON userdemo.* TO userdemo@localhost identified by '<your_password>';
quit
```

Run database migrations to intialize database schema:

```
./vendor/bin/doctrine-module migrations:migrate
```

Then create an Apache virtual host. It should look like below:

```
<VirtualHost *:80>
    DocumentRoot /path/to/userdemo/public
    
	<Directory /path/to/userdemo/public/>
        DirectoryIndex index.php
        AllowOverride All
        Require all granted
    </Directory>

</VirtualHost>
```

Now you should be able to see the User Demo website by visiting the link "http://localhost/". 
 
## License

This code is provided under the [BSD-like license](https://en.wikipedia.org/wiki/BSD_licenses). 

## Contributing

If you found a mistake or a bug, please report it using the [Issues](https://github.com/olegkrivtsov/using-zf3-book-samples/issues) page. 
Your feedback is highly appreciated.
