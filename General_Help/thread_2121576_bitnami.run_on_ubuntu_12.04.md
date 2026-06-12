---
title: "bitnami.run on ubuntu 12.04"
date: 2013-03-02
forum: General Help
---

### Post by miikaa on 2013-03-02
Hi,
i just installed ubuntu 12.04 on my lap .also currently am Learning  PHP  so am trying to get bitnami.run to install but can't !! 
 is there some help !!! ^_^

---

### Post by miikaa on 2013-03-02
hi 
 i am having trouble in installing some program that has a .run file "bitnami.run  . 
any advice ??

---

### Post by dabl on 2013-03-02
> **miikaa said:**
> hi 
 i am having trouble in installing some program that has a .run file "bitnami.run  . 
any advice ??

Not sure what you mean by "trouble".  If that .run file is in fact an installer, then the typical command to run it, at the directory prompt where the file is located, would be ```
sh ./bitnami.run
```

---

### Post by tgalati4 on 2013-03-02
If bitnami.run is an install script, then it probably needs to be marked as executable.  Scripts are not executable by default as a security precaution.  It requires an active effort on your part to be able to run it.

```
cd directorywherebinamiscriptfileislocated
sudo chmod +x bitnami.run
./bitnami.run

or

sudo ./bitnami.run
```

I'm not sure if the bitnami stack installer requires root (sudo) privileges or not.

Realize that PHP5 is part of the Ubuntu repositories, so unless you are trying to install something specific (and not in the repositories), you should first use the repositories:

tgalati4@Mint14-Extensa ~ $ apt-cache search php5
libapache2-mod-php5 - server-side, HTML-embedded scripting language (Apache 2 module)
php5 - server-side, HTML-embedded scripting language (metapackage)
php5-cgi - server-side, HTML-embedded scripting language (CGI binary)
php5-cli - command-line interpreter for the php5 scripting language
php5-common - Common files for packages built from the php5 source
php5-curl - CURL module for php5
php5-dbg - Debug symbols for PHP5
php5-dev - Files for PHP5 module development
php5-gd - GD module for php5
php5-gmp - GMP module for php5
php5-ldap - LDAP module for php5
php5-mysql - MySQL module for php5
php5-odbc - ODBC module for php5
php5-pgsql - PostgreSQL module for php5
php5-pspell - pspell module for php5
php5-recode - recode module for php5
php5-snmp - SNMP module for php5
php5-sqlite - SQLite module for php5
php5-tidy - tidy module for php5
php5-xmlrpc - XML-RPC module for php5
php5-xsl - XSL module for php5
cakephp - MVC rapid application development framework for PHP
dwoo - PHP5 template engine
jffnms - web-based Network Management System (NMS) for IP networks
libapache2-mod-php5filter - server-side, HTML-embedded scripting language (apache 2 filter module)
libexpect-php5 - expect module for PHP 5
libgv-php5 - PHP5 bindings for graphviz
libkohana2-modules-php - lightweight PHP5 MVC framework (extension modules)
libkohana2-php - lightweight PHP5 MVC framework
libkohana3.1-core-php - PHP5 framework core classes
libkohana3.1-php - PHP5 framework metapackage
libkohana3.2-core-php - PHP5 framework core classes
libkohana3.2-php - PHP5 framework metapackage
libow-php5 - Dallas 1-wire support: PHP5 bindings
libphp-jpgraph - Object oriented graph library for php5
libphp-jpgraph-examples - Object oriented graph library for php5 (examples)
libphp5-embed - HTML-embedded scripting language (Embedded SAPI library)
php-auth - PHP PEAR modules for creating an authentication system
php-codesniffer - PHP, CSS and JavaScript coding standard analyzer and checker
php-doc - Documentation for PHP5
php-imlib - PHP Imlib2 Extension
php5-adodb - Extension optimising the ADOdb database abstraction library
php5-enchant - Enchant module for php5
php5-exactimage - fast image manipulation library (PHP bindings)
php5-ffmpeg - audio and video support via ffmpeg for php5
php5-fpm - server-side, HTML-embedded scripting language (FPM-CGI binary)
php5-gdcm - Grassroots DICOM PHP5 bindings
php5-geoip - GeoIP module for php5
php5-imagick - ImageMagick module for php5
php5-imap - IMAP module for php5
php5-interbase - interbase/firebird module for php5
php5-intl - internationalisation module for php5
php5-lasso - Library for Liberty Alliance and SAML protocols - PHP 5 bindings
php5-librdf - PHP5 language bindings for the Redland RDF library
php5-mapscript - php5-cgi module for MapServer
php5-mcrypt - MCrypt module for php5
php5-memcache - memcache extension module for PHP5
php5-memcached - memcached extension module for PHP5, uses libmemcached
php5-midgard2 - Midgard2 Content Repository - PHP5 language bindings and module
php5-ming - Ming module for php5
php5-mongo - MongoDB database driver
php5-mysqlnd - MySQL module for php5 (Native Driver)
php5-ps - ps module for PHP 5
php5-radius - PECL radius module for PHP 5
php5-remctl - PECL module for Kerberos-authenticated command execution
php5-rrd - rrd module for PHP 5
php5-sasl - Cyrus SASL extension for PHP 5
php5-suhosin - advanced protection module for php5
php5-svn - PHP Bindings for the Subversion Revision control system
php5-sybase - Sybase / MS SQL Server module for php5
php5-tokyo-tyrant - PHP interface to Tokyo Cabinet's network interface, Tokyo Tyrant
php5-vtkgdcm - Grassroots DICOM VTK PHP bindings
php5-xcache - Fast, stable PHP opcode cacher
php5-xdebug - Xdebug Module for PHP 5
phpunit - Unit testing suite for PHP5

---

### Post by miikaa on 2013-03-02
> **dabl said:**
> Not sure what you mean by "trouble".  If that .run file is in fact an installer, then the typical command to run it, at the directory prompt where the file is located, would be ```
sh ./bitnami.run
```

i did it namy time 
"sudo ./bitnami.run" 
and the file is installed on my desktop  
but it gave me 
"sudo: ./bitnami.run: command not found "

---

### Post by miikaa on 2013-03-02
ok look i open properties and marked on make it executable , 
i did it before but i think the stack was corrupted so i del. and download another one and nw its working thanks

---

### Post by gordintoronto on 2013-03-02
Further reading:
[http://bitnami.org/stack/redmine/README.txt](http://bitnami.org/stack/redmine/README.txt)

---

### Post by sffvba[e0rt on 2013-03-03
*Threads **merged** and **moved** to General Help.*


404

---

