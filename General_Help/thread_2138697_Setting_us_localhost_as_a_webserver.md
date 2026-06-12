---
title: "Setting us localhost as a webserver"
date: 2013-04-25
forum: General Help
---

### Post by syedk01 on 2013-04-25
I am trying to set up a package (Text mine) to run as web based interface on a Ubuntu 12.04 LTS desktop.


 To use the web based interface load the [http://host/cgi-bin/????/co_login.pl](http://host/cgi-bin/????/co_login.pl) script

1. My question is what should be the exact syntax of the above ie what is the "host' equal to?

2. Do I need to type the full directory path name?
 3. is it [http://localhost/home/syedk/TEXT/textmine-0.21/cgi-bin/co-login.pl?](http://localhost/home/syedk/TEXT/textmine-0.21/cgi-bin/co-login.pl?)

My hostname is Hxxx

My home directory is /home/syedk

The Text mine package is located on /home/syedk/TEXT/textmine-021

/TEXT/textmine-0.21$ ls -l
total 64
drwxr-xr-x 2 syedk syedk 4096 May 17  2008 cgi-bin
-rw-r--r-- 1 syedk syedk  512 Jan  7  2008 Copyright
drwxr-xr-x 3 syedk syedk 4096 Sep 29  2007 docs
drwxr-xr-x 3 syedk syedk 4096 Jul 30  2008 icons
-rw-r--r-- 1 syedk syedk 2606 Jan  7  2008 INSTALL
-rw-r--r-- 1 syedk syedk  378 Sep 29  2007 install.bat
-rw-r--r-- 1 syedk syedk  732 Sep 29  2007 install.sh
drwxr-xr-x 2 syedk syedk 4096 Sep 29  2007 lsi
-rw-r--r-- 1 syedk syedk 1028 Sep 29  2007 Manifest
-rw-r--r-- 1 syedk syedk 6207 Jan  7  2008 Release
drwxr-xr-x 2 syedk syedk 4096 Jan  7  2008 t
drwxr-xr-x 2 syedk syedk 4096 Apr 24 12:13 TextMine
drwxr-xr-x 2 syedk syedk 4096 Oct  4  2007 tmp
drwxr-xr-x 6 syedk syedk 4096 Sep 29  2007 tools
drwxr-xr-x 3 syedk syedk 4096 Jul 30  2008 utils


/etc/apache2/sites-available/default


<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>




>>>>>apache2 error log snippet<>>>>>>>>>>>>>>>

127.0.0.1 - - [22/Apr/2013:19:09:24 -1000] "GET /home/syedk/TEXT/textmine-0.21/c
gi-bin/co_login.pl HTTP/1.1" 404 529 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; 
rv:20.0) Gecko/20100101 Firefox/20.0"

---

