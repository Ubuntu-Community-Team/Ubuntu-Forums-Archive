---
title: "PHP5 from apt-get and PDO"
date: 2007-02-18
forum: General Help
---

### Post by SirBob1701 on 2007-02-18
I was wondering if anyone knows how to get the PDO classes installed for PHP5 because it seems that they were not installed when I did an apt-get for php5.  Will I have to manually compile it or is their a repository for this?

---

### Post by Gibbs on 2007-02-18
System > Administration > Synaptic Package Manager

Use the search feature and search for "php-db". It should be the first result.

---

### Post by SirBob1701 on 2007-02-20
what i see for php-db is PHP PEAR Database Abstraction Layer which I was told in freenode is not the pdo package.

---

### Post by theh0g on 2007-02-21
I had this problem just yesterday (and yes, php-db installation is...useless). I dunno EXACTLY what I did, but I've installed php5-dev, mysqlclient15-dev (or something) and then ran PECL INSTALL PDO and PECL INSTALL PDO_MYSQL. Seems to work, but it wont parse queries on execute (replacing ? with data from array) yet. Hope that helps.

EDIT: oh yeah, don't forget to add both extensions to php.ini (pdo.so and pdo_mysql.so)

---

### Post by Roland Bouman on 2007-03-05
Here's a more exact description to install pdo on top of the php5 packages provided by ubuntu (so this procedure assumes you already installed php and a webserver):

1) make sure you install the ubuntu package php-pear. I used synaptic for that but the command line should work too of course:

```

sudo apt-get install php-pear

```

Now you have to extra executables to work with php's own packaging system, pear and pecl

2) install pdo:

```

sudo pecl install pdo

```

This will check your build environment and actually install plain pdo. If everything goes well, it ends in something like:

```

Build process completed successfully
Installing '/var/tmp/pear-build-root/install-PDO-1.0.3//usr/lib/php5/20051025/pdo.so'
Installing '/var/tmp/pear-build-root/install-PDO-1.0.3//usr/include/php/ext/pdo/php_pdo.h'
Installing '/var/tmp/pear-build-root/install-PDO-1.0.3//usr/include/php/ext/pdo/php_pdo_driver.h'
install ok: channel://pecl.php.net/PDO-1.0.3
You should add "extension=pdo.so" to php.ini

```

3) install any pdo drivers. 

Check the php documentation to find out your prerequisites. For example, to install pdo_mysql, I first installed the mysql php extension:

```

sudo apt-get install php5-mysql

```

(For some reason, this seemed to pull php5-mysqli along too)
After that, install the pdo_mysql package again using the php packaging system rather than the ubuntu packages:

```

sudo pecl install pdo_mysql

```

Again, you get an enormous listing which is output of the installation process:

```

Build process completed successfully
Installing '/var/tmp/pear-build-root/install-PDO_MYSQL-1.0.2//usr/lib/php5/20051025/pdo_mysql.so'
install ok: channel://pecl.php.net/PDO_MYSQL-1.0.2
You should add "extension=pdo_mysql.so" to php.ini

```

4) find and edit your php.ini to add the extensions in the configuration. I found my php.ini using the phpinfo() function (which outputs a webpage with the php environment). I used kedit but of  course, any text editor will do:

```

sudo kedit /etc/php5/apache2/php.ini

```

5) add the line for the pdo extension and the specific drivers to the php.ini file, and save the file:

```

extension=pdo.so
extension=pdo_mysql.so

```

(I first searched php.ini for 'extension' and put those lines right beneath the example lines for adding an extension

6) Restart apache to let the changes take effect:

```

cd /etc/init.d
sudo apache2 -k restart

```

This worked for me.

Good luck, and kind regards

Roland

---

### Post by relix on 2007-03-25
I'd like to add to that:

if you get an error "phpize not found" after trying to install pdo through pecl (sudo pecl install pdo), you should install the php5-dev package.

```
sudo apt-get install php5-dev
```

if you get the following error while trying to install pdo_mysql:

```
checking for MySQL support for PDO... yes, shared
checking for mysql_config... not found
configure: error: Cannot find MySQL header files under
ERROR: `/tmp/tmpRiQ5ax/PDO_MYSQL-1.0.2/configure' failed

```

you should install the following package:
```

sudo apt-get install libmysqlclient15-dev

```

(I got them both)

---

