---
title: "he CURL library is NOT loaded in php.ini??????"
date: 2013-03-26
forum: General Help
---

### Post by caleb12134 on 2013-03-26
[COLOR=#000000]Upon installing SpaceBukkit Minecraft admin panel i get this ????[/COLOR]

[COLOR=#555555][FONT=Ubuntu][COLOR=#B94A48][FONT=inherit]The [COLOR=#417394]CURL[/COLOR] library is NOT loaded in your php.ini![/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000]What does this mean??? I have apache2 on my poweredge???? How do i fix dis??? Please help.. thanks [/COLOR]:smile:

SOmeone said this "[COLOR=#000000][INDENT]The stock PHP installation does not include all the myriad modules that PHP supports. To add support for [COLOR=#417394]CURL[/COLOR], [install]("http://ubuntuforums.org/#") the **php5-curl** package. To see a list of the various modules available, look for packages with names like php5-*. A quick list is available by running "apt-cache search php5-*" at a command prompt"
[/INDENT]
[/COLOR]

And here are the results for the command "[COLOR=#000000]apt-cache search php5-*"

[/COLOR][COLOR=#000000]root@ubuntu:~# apt-cache search php5-*[/COLOR]
[COLOR=#000000]libapache2-mod-php5 - server-side, HTML-embedded scripting language (Apache 2 module)[/COLOR]
[COLOR=#000000]php-pear - PEAR - PHP Extension and [/COLOR][Application]("http://ubuntuforums.org/#")[COLOR=#000000] Repository[/COLOR]
[COLOR=#000000]php5 - server-side, HTML-embedded scripting language (metapackage)[/COLOR]
[COLOR=#000000]php5-cgi - server-side, HTML-embedded scripting language (CGI binary)[/COLOR]
[COLOR=#000000]php5-cli - command-line interpreter for the php5 scripting language[/COLOR]
[COLOR=#000000]php5-common - Common files for packages built from the php5 source[/COLOR]
[COLOR=#000000]php5-curl - [/COLOR][COLOR=#417394]CURL[/COLOR][COLOR=#000000] module for php5[/COLOR]
[COLOR=#000000]php5-dbg - Debug symbols for PHP5[/COLOR]
[COLOR=#000000]php5-dev - Files for PHP5 module development[/COLOR]
[COLOR=#000000]php5-gd - GD module for php5[/COLOR]
[COLOR=#000000]php5-gmp - GMP module for php5[/COLOR]
[COLOR=#000000]php5-ldap - LDAP module for php5[/COLOR]
[COLOR=#000000]php5-mysql - MySQL module for php5[/COLOR]
[COLOR=#000000]php5-odbc - ODBC module for php5[/COLOR]
[COLOR=#000000]php5-pgsql - PostgreSQL module for php5[/COLOR]
[COLOR=#000000]php5-pspell - pspell module for php5[/COLOR]
[COLOR=#000000]php5-recode - recode module for php5[/COLOR]
[COLOR=#000000]php5-snmp - SNMP module for php5[/COLOR]
[COLOR=#000000]php5-sqlite - SQLite module for php5[/COLOR]
[COLOR=#000000]php5-tidy - tidy module for php5[/COLOR]
[COLOR=#000000]php5-xmlrpc - XML-RPC module for php5[/COLOR]
[COLOR=#000000]php5-xsl - XSL module for php5[/COLOR]
[COLOR=#000000]cakephp - MVC [/COLOR][rapid application development]("http://ubuntuforums.org/#")[COLOR=#000000] framework for PHP[/COLOR]
[COLOR=#000000]dwoo - PHP5 template engine[/COLOR]
[COLOR=#000000]jffnms - web-based [/COLOR][Network Management]("http://ubuntuforums.org/#")[COLOR=#000000] System (NMS) for IP networks[/COLOR]
[COLOR=#000000]libapache2-mod-php5filter - server-side, HTML-embedded scripting language (apache 2 filter module)[/COLOR]
[COLOR=#000000]libexpect-php5 - expect module for PHP 5[/COLOR]
[COLOR=#000000]libgv-php5 - PHP5 bindings for graphviz[/COLOR]
[COLOR=#000000]libkohana2-modules-php - lightweight PHP5 MVC framework (extension modules)[/COLOR]
[COLOR=#000000]libkohana2-php - lightweight PHP5 MVC framework[/COLOR]
[COLOR=#000000]libkohana3.1-core-php - PHP5 framework core [/COLOR][classes]("http://ubuntuforums.org/#")
[COLOR=#000000]libkohana3.1-php - PHP5 framework metapackage[/COLOR]
[COLOR=#000000]libkohana3.2-core-php - PHP5 framework core classes[/COLOR]
[COLOR=#000000]libkohana3.2-php - PHP5 framework metapackage[/COLOR]
[COLOR=#000000]libow-php5 - Dallas 1-wire support: PHP5 bindings[/COLOR]
[COLOR=#000000]libphp-jpgraph - Object oriented graph library for php5[/COLOR]
[COLOR=#000000]libphp-jpgraph-examples - Object oriented graph library for php5 (examples)[/COLOR]
[COLOR=#000000]php-auth - PHP PEAR modules for creating an authentication system[/COLOR]
[COLOR=#000000]php-codesniffer - tokenises PHP code and detects violations of a defined set of coding standards[/COLOR]
[COLOR=#000000]php-doc - Documentation for PHP5[/COLOR]
[COLOR=#000000]php-imlib - PHP Imlib2 Extension[/COLOR]
[COLOR=#000000]php5-adodb - Extension optimising the ADOdb database abstraction library[/COLOR]
[COLOR=#000000]php5-auth-pam - A PHP5 extension for PAM authentication[/COLOR]
[COLOR=#000000]php5-enchant - Enchant module for php5[/COLOR]
[COLOR=#000000]php5-exactimage - fast image manipulation library (PHP bindings)[/COLOR]
[COLOR=#000000]php5-ffmpeg - audio and video support via ffmpeg for php5[/COLOR]
[COLOR=#000000]php5-fpm - server-side, HTML-embedded scripting language (FPM-CGI binary)[/COLOR]
[COLOR=#000000]php5-geoip - GeoIP module for php5[/COLOR]
[COLOR=#000000]php5-imagick - ImageMagick module for php5[/COLOR]
[COLOR=#000000]php5-imap - IMAP module for php5[/COLOR]
[COLOR=#000000]php5-interbase - interbase/firebird module for php5[/COLOR]
[COLOR=#000000]php5-intl - internationalisation module for php5[/COLOR]
[COLOR=#000000]php5-lasso - Library for Liberty Alliance and SAML protocols - PHP 5 bindings[/COLOR]
[COLOR=#000000]php5-librdf - PHP5 language bindings for the Redland RDF library[/COLOR]
[COLOR=#000000]php5-mapscript - php5-cgi module for MapServer[/COLOR]
[COLOR=#000000]php5-mcrypt - MCrypt module for php5[/COLOR]
[COLOR=#000000]php5-memcache - memcache extension module for PHP5[/COLOR]
[COLOR=#000000]php5-memcached - memcached extension module for PHP5, uses libmemcached[/COLOR]
[COLOR=#000000]php5-midgard2 - Midgard2 Content Repository - PHP5 language bindings and module[/COLOR]
[COLOR=#000000]php5-ming - Ming module for php5[/COLOR]
[COLOR=#000000]php5-mysqlnd - MySQL module for php5 (Native Driver)[/COLOR]
[COLOR=#000000]php5-ps - ps module for PHP 5[/COLOR]
[COLOR=#000000]php5-radius - PECL radius module for PHP 5[/COLOR]
[COLOR=#000000]php5-remctl - PECL module for Kerberos-authenticated command execution[/COLOR]
[COLOR=#000000]php5-rrd - rrd module for PHP 5[/COLOR]
[COLOR=#000000]php5-sasl - Cyrus SASL extension for PHP 5[/COLOR]
[COLOR=#000000]php5-suhosin - advanced protection module for php5[/COLOR]
[COLOR=#000000]php5-svn - PHP Bindings for the Subversion Revision control system[/COLOR]
[COLOR=#000000]php5-sybase - Sybase / MS SQL Server module for php5[/COLOR]
[COLOR=#000000]php5-tokyo-tyrant - PHP interface to Tokyo Cabinet's network interface, Tokyo Tyrant[/COLOR]
[COLOR=#000000]php5-uuid - OSSP uuid module for php5[/COLOR]
[COLOR=#000000]php5-xcache - Fast, stable PHP opcode cacher[/COLOR]
[COLOR=#000000]php5-xdebug - Xdebug Module for PHP 5[/COLOR]
[COLOR=#000000]phpunit - Unit testing suite for PHP5[/COLOR]
[COLOR=#000000]root@ubuntu:~#[/COLOR]

---

### Post by Elfy on 2013-03-26
Thread closed. Please do not post duplicates, it dilutes community effort.

---

