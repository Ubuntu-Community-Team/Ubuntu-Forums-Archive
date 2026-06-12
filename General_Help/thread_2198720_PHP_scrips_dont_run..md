---
title: "PHP scrips dont run."
date: 2014-01-10
forum: General Help
---

### Post by adam17 on 2014-01-10
Hi, 

I have noticed a few times when building websites and visiting some web pages that when I use a contact form with a PHP script behind it ubuntu seems to try and open the file with a dialogue box appearing stating that there is not software installed to run php rather that the script being run like it does on my windows machine. is there something I need to install to enable this to work?

Thanks in advance 

Adam

---

### Post by SeijiSensei on 2014-01-10
On Ubuntu, the code to enable PHP is contained in the package **libapache2-mod-php5**.  It adds two files to /etc/apache2/mods-available/, php5.conf and php5.load, and creates symbolic links to those files in /etc/apache2/mods-enabled/.  Look at the code in php5.conf.  It begins with 

```

<FilesMatch ".+\.ph(p[345]?|t|tml)$">
    SetHandler application/x-httpd-php
</FilesMatch>

```

which tells Apache to invoke the PHP module, loaded in php5.load, for files ending in appropriate extensions like .php, .php5, .php?, or the very old .phtml.  (The matching template is a "[regular expression]("http://en.wikipedia.org/wiki/Regular_expression#POSIX_basic_and_extended").")

I don't know whether you are in charge of the server on which your scripts are run.  But if you use an Ubuntu server, make sure you have these files.  If not, install the libapache2-mod-php5 package, or use [tasksel]("https://help.ubuntu.com/community/ApacheMySQLPHP") to install Apache2, PHP5, and MySQL5.

---

### Post by adam17 on 2014-01-10
Hi SeijiSensei, 

I used the command sudo apt-get install **libapache2-mod-php5** in the terminal and I am now able to access websites that use PHP.

Thankyou so much for your help!

Regards.

Adam

---

