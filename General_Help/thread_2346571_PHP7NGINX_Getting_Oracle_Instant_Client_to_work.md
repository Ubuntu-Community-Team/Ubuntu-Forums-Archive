---
title: "PHP7/NGINX Getting Oracle Instant Client to work"
date: 2016-12-16
forum: General Help
---

### Post by thepunisher2 on 2016-12-16
Ubuntu 16.04.1 LTS
PHP 7.0.8
NGINX 1.10.0

Here is what I have tried to get the Oracle Instant Client working:
Get all essential packages for download and compiling from PEAR repositories:
$ sudo apt-get install php-cli php-db unzip php-pear php-dev build-essential libaio1

First step: Install the Oracle Client
Execute the following commands in your terminal:
$ sudo mkdir -p /opt/oracle/instantclient
$ sudo -i << switches to root!

Unzip files executing these commands:
$ unzip /opt/oracle/instantclient/instantclient-basic-linux.x64-12.1.0.2.0.zip
$ unzip /opt/oracle/instantclient/instantclient-sdk-linux.x64-12.1.0.2.0.zip

Move all instantclient content to /opt/oracle/instantclient:
$ mv instantclient_12_1/* /opt/oracle/instantclient/

During extension compiling, some errors will arise when linking with some libraries. To avoid them, do:
$ ln -s libclntsh.so.* libclntsh.so
$ ln -s libocci.so.* libocci.so
$ echo /opt/oracle/instantclient >> /etc/ld.so.conf
$ ldconfig

Create a folder for your network configuration files
$ mkdir -p network/admin

Place sqlnet.ora and tnsnames.ora files in /opt/oracle/instantclient/network/admin
Now you have the basic connection kit for connections and SDK for compiling PHP extensions.
Second step: Install the OCI8 PHP Extension
Request OCI8 install:
$ sudo pecl install oci8

Type instantclient,/opt/oracle/instantclient when prompted for Instant Client path.
ln -s /etc/php/7.0/mods-available/oci8.ini /etc/php/7.0/fpm/conf.d/20-oci8.ini
service php7.0-fpm restart
Now you have all oci_* functions available for PHP in both php-cli and Nginx

I create this php page:
[PHP]<?php
oci_connect("USER", "PWORD", "test");
?>[/PHP]

I get this error when going to it:
```

2016/12/16 09:17:19 [error] 2796#2796: *3 FastCGI sent in stderr: "PHP message: PHP Warning:  oci_connect(): OCIEnvNlsCreate() failed. There is something wrong with your system - please check that LD_LIBRARY_PATH includes the directory with Oracle Instant Client libraries in /var/www/html/test2.php on line 2
PHP message: PHP Stack trace:
PHP message: PHP   1. {main}() /var/www/html/test2.php:0
PHP message: PHP   2. oci_connect() /var/www/html/test2.php:2
PHP message: PHP Warning:  oci_connect(): Error while trying to retrieve text for error ORA-01804
 in /var/www/html/test2.php on line 2
PHP message: PHP Stack trace:
PHP message: PHP   1. {main}() /var/www/html/test2.php:0

```

One question I have is about the "lib" folder. I do not have a "lib" folder in /opt/oracle/instantclient/, I am not sure if I am supposed to or not.
The other one is how in the world do you set the LD_LIBRARY_PATH variable with the setup I have?

I have tried everywhere I can think of, and I can not get it to show the LD_LIBRARY_PATH variable when I load a php page with phpinfo();

Thanks

---

### Post by thepunisher2 on 2016-12-16
I got the variables to show finally in phpinfo() by doing this:

Insert the following at the bottom of this: /etc/php/7.0/fpm/pool.d/www.conf
```
env[ORACLE_HOME] = /opt/oracle/instantclient
env[LD_LIBRARY_PATH] = /opt/oracle/instantclient
```

service php7.0-fpm restart

Still getting the same error message.

---

### Post by thepunisher2 on 2016-12-16
Got it going:

Get all essential packages for download and compiling from PEAR repositories:
$ sudo -i
$ apt-get update
$ apt-get upgrade
$ apt-get install php-cli php-db unzip php-pear php-dev build-essential libaio1 alien
First step: Install the Oracle Client
Download the 64bit rpms from oracles site:
oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm
oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm
Convert the rpm files and install
$ alien -i oracle-instantclient*-basic-*.rpm
$ alien -i oracle-instantclient*-devel-*.rpm
It installed to: 
/usr/lib/oracle/12.1/client64
/usr/lib/oracle/12.1/client64/lib
/etc/php/7.0/fpm/pool.d/www.conf
env[ORACLE_HOME] = /usr/lib/oracle/12.1/client64
env[LD_LIBRARY_PATH] = /usr/lib/oracle/12.1/client64/lib
service php7.0-fpm restart
pecl install oci8
instantclient,/usr/lib/oracle/12.1/client64/lib
Installing '/usr/lib/php/20151012/oci8.so'
install ok: channel://pecl.php.net/oci8-2.1.3
configuration option "php_ini" is not set to php.ini location
You should add "extension=oci8.so" to php.ini
^^ Add "extension=oci8.so" to /etc/php/7.0/fpm/php.ini
service php7.0-fpm restart
Create phpinfo() page to verify OCI8 is enabled, ORACLE_HOME and LD_LIBRARY_PATH variables are set.
Try oci_connect test:
<?php
oci_connect("USER", "PWORD", "SERVERIP/name");
?>

---

