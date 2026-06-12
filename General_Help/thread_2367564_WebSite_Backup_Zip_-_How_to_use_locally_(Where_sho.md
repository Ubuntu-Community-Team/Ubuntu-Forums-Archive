---
title: "WebSite Backup Zip - How to use locally (Where should I ask this question?)"
date: 2017-07-31
forum: General Help
---

### Post by Alan5127 on 2017-07-31
Hi All,

I am reasonably au fait with computers and IT in general, but not so much with web servers.

I have been given a zip file backup of our website by the developer, and I would like to set it up on my Ubuntu machine so that I can 'have a play' (this won't go back into production or be exposed to the internet - it is just that I am interested).

I have setup Apache2, MySQL, PHP, and PHPMyAdmin on my machine, and it is all (seemingly) working fine with my 'Hello World' (index.php) sitting in /var/www/html/.

However, I don't know where to go from here, and I am not really sure if I am asking the question in the right place!

Not sure if it helps, but the root of the zip files contains this (ls -la):

```

drwxrwxrwx 1 root root   2408 Aug  1 15:18 .
drwxrwxrwx 1 root root  12288 Aug  1 15:18 ..
drwxrwxrwx 1 root root      0 Mar  8 10:57 app
-rwxrwxrwx 1 root root   1646 Mar  8 10:57 artisan
drwxrwxrwx 1 root root      0 Mar  8 10:57 bootstrap
-rwxrwxrwx 1 root root   1548 Mar  8 10:57 composer.json
-rwxrwxrwx 1 root root 151002 Mar  8 10:57 composer.lock
drwxrwxrwx 1 root root      0 Mar  8 10:57 config
drwxrwxrwx 1 root root      0 Mar  8 10:57 database
-rwxrwxrwx 1 root root   6148 Mar  8 10:57 .DS_Store
-rwxrwxrwx 1 root root     61 Mar  8 10:57 .gitattributes
-rwxrwxrwx 1 root root    113 Mar  8 10:57 .gitignore
-rwxrwxrwx 1 root root    567 Mar  8 10:57 gulpfile.js
-rwxrwxrwx 1 root root    402 Mar  8 10:57 package.json
-rwxrwxrwx 1 root root    930 Mar  8 10:57 phpunit.xml
drwxrwxrwx 1 root root      0 Mar  8 10:57 public
-rwxrwxrwx 1 root root   2208 Mar  8 10:57 readme.md
drwxrwxrwx 1 root root      0 Mar  8 10:57 resources
drwxrwxrwx 1 root root      0 Mar  8 10:57 routes
-rwxrwxrwx 1 root root    563 Mar  8 10:57 server.php
drwxrwxrwx 1 root root      0 Mar  8 10:57 storage
drwxrwxrwx 1 root root      0 Mar  8 10:57 tests
-rwxrwxrwx 1 root root    115 Mar  8 10:57 update.sh
-rwxrwxrwx 1 root root 147042 Mar  8 10:57 yarn.lock
```

The /public/ directory contains:

```
drwxrwxrwx 1 root root    0 Mar  8 10:57 .
drwxrwxrwx 1 root root 2408 Aug  1 15:18 ..
drwxrwxrwx 1 root root    0 Mar  8 10:57 build
drwxrwxrwx 1 root root    0 Mar  8 10:57 css
-rwxrwxrwx 1 root root 6148 Mar  8 10:57 .DS_Store
-rwxrwxrwx 1 root root    0 Mar  8 10:57 favicon.ico
drwxrwxrwx 1 root root    0 Mar  8 10:57 fonts
-rwxrwxrwx 1 root root  553 Mar  8 10:57 .htaccess
drwxrwxrwx 1 root root    0 Mar  8 10:57 img
-rwxrwxrwx 1 root root 1782 Mar  8 10:57 index.php
drwxrwxrwx 1 root root    0 Mar  8 10:57 js
-rwxrwxrwx 1 root root   24 Mar  8 10:57 robots.txt
-rwxrwxrwx 1 root root  914 Mar  8 10:57 web.config
```


Can anyone point me to how to fire this up locally on my machine, or alternatively, tell me where to go (in the nicest possible sense) to ask this question?

Thanks,

Alan.

---

### Post by dragonfly41 on 2017-08-01
Reviewing your web file system it does look very familiar.
It follows the broad structure of a laravel web site (which I happen to be developing on my localhost before deployment to the cloud).

Although you can deploy index.php to render "hello world" that is a bit of a decoy.

> I have setup Apache2, MySQL, PHP, and PHPMyAdmin on my machine, and it is all (seemingly) working fine with my 'Hello World' (index.php) sitting in /var/www/html/.

The document base is in the public folder in /var/www/html/public/.

...

To understand more about laravel go here. Latest version is 5.4.

[https://laravel.com/](https://laravel.com/)

Be prepared for a steep learning curve.

Click the Laracasts tab at top of above home page to get into tutorials (many of the starter tutorials are free so you don't need to sign up for courses).

You will need to run through the installation of composer.

I would start quite separately from the zipped filesystem and as a learning exercise create your own local laravel &#8220;hello world&#8221; site by following installation instructions here.

[https://laravel.com/docs/5.4](https://laravel.com/docs/5.4)


Read here ...


> **Installing Laravel**

Laravel utilizes [Composer]("https://getcomposer.org/") to manage its dependencies. So, before using Laravel, make sure you have Composer installed on your machine.


[https://getcomposer.org/](https://getcomposer.org/)

Also do take note of apache2 server requirements listed here ...

[https://laravel.com/docs/5.4](https://laravel.com/docs/5.4)

...

If you look carefully at your zipped web site structure you will see these files ...

 ```
artisan
 composer.json
```
 
 These are clues that you need composer and that this is a laravel created site.
 
 
 When you have built your first laravel site you can then go back to your developer's folder and see how to get your site working.
 
 I build my (multiple) test sites as virtual hosts on Ubuntu 16.04.
 
 
 In /etc/apache2/sites-available I have laravel5.dev.conf (one conf file for each virtual host).  Use this as an example and customise for your needs.
 
```


<VirtualHost *:80>
    ServerName laravel5.dev
    ServerAlias [www.laravel5.dev]("http://www.laravel5.dev")
    ServerAdmin [EMAIL="yourname@yourmailserver.com"]yourname@yourmailserver.com[/EMAIL]
        
    DocumentRoot /var/www/html/laravel5.dev/public
    # DirectoryIndex index.php index.html
    
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    
    <Directory /var/www/html/laravel5.dev/public >
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Require all granted
        Order allow,deny
        allow from all                        
    </Directory>

# log format options
# [http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats)

    LogLevel warn
    ErrorLog ${APACHE_LOG_DIR}/laravel5.dev/error.log
    CustomLog ${APACHE_LOG_DIR}/laravel5.dev/access.log combined

</VirtualHost>
 
 
```
 
 
 To get your virtual host working you need to enable the site first
 
 ```
sudo a2ensite laravel5.dev
```
 
 This creates a link in /etc/apache2/sites-enabled folder.
 
 Next you need to add new logs folder in /var/log/apache2/ directory.
 
 ```
 /var/log/apache2/laravel5.dev
```
  
  which will write virtual host logs to error.log and access.log.
  
 Next you need to add your virtual host domain name &#8220;laravel.dev&#8221; into file ..

/etc/hosts
 
```

127.0.0.1 localhost 
127.0.0.1 laravel5.dev [www.laravel5.dev]("http://www.laravel5.dev") 

```

Finally restart apache2.

You should be able to navigate to [http://laravel5.dev](http://laravel5.dev) in your browser.
Or the alias [http://www.laravel5.dev]("http://www.larave5.dev")


*Note that in the description above you can change &#8220;laravel5.dev&#8221; to any name you wish .. &#8220;mywebsite&#8221;.*

No doubt you will experience teething problems with first test site but these are usually permissions settings. Look through the laravel forum for more understanding.

When you have finished this learning process you should be able to talk more with your developer who should confirm that this is a laravel site (hopefully version 5.4 and not version 4.x).


**[Later edit]**

If you open composer.json in an editor (geany or gedit) you can see what version laravel is used ..
here is an snippet ..

```

{
    "name": "laravel/laravel",
    "description": "The Laravel Framework.",
    "keywords": ["framework", "laravel"],
    "license": "MIT",
    "type": "project",
    "require": {
        "laravel/framework": "5.4.*",
        "laravelcollective/html": "~5.4"

...   ...


```


And as a further suggestion.  You could ask your developer to place the website into a private github site and then download into your localhost environment to be rebuilt.

[https://laracasts.com/discuss/channels/laravel/how-to-open-downloaded-laravel-projects-from-github-on-localhost-xampp?page=1](https://laracasts.com/discuss/channels/laravel/how-to-open-downloaded-laravel-projects-from-github-on-localhost-xampp?page=1)

You could then stay in sync with development.

---

### Post by Alan5127 on 2017-08-01
Hi [**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878"),

Awesome post - thank you!

I will investigate Laravel and Composer, and probably post back after doing that.

Thanks,

Alan.

---

