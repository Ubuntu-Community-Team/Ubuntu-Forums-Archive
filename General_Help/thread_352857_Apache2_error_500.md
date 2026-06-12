---
title: "Apache2 error 500"
date: 2007-02-03
forum: General Help
---

### Post by jae1227 on 2007-02-03
I went to install libapache2-mod-python2.4 and after i installed and restarted apache I got this error:

```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.0.55 (Ubuntu) Server at localhost Port 80

```

I did not know what to do. My default website setup looks like this. Hope someone can help. ```


NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	     <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
             </Directory>
	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by jae1227 on 2007-02-04
This is my error.log

```
[Sun Jan 28 07:37:16 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sun Jan 28 08:17:45 2007] [error] [client 127.0.1.1] File does not exist: /var/www/announce
[Sun Jan 28 08:29:03 2007] [error] [client 127.0.1.1] File does not exist: /var/www/announce
[Sun Jan 28 11:01:38 2007] [error] [client 127.0.1.1] File does not exist: /var/www/announce
[Sun Jan 28 11:01:58 2007] [error] [client 127.0.1.1] File does not exist: /var/www/scrape
[Sun Jan 28 11:11:59 2007] [error] [client 127.0.1.1] File does not exist: /var/www/scrape
[Sun Jan 28 11:12:53 2007] [error] [client 127.0.1.1] File does not exist: /var/www/announce
[Sun Jan 28 11:16:35 2007] [error] [client 127.0.1.1] File does not exist: /var/www/announce
[Sun Jan 28 11:22:00 2007] [error] [client 127.0.1.1] File does not exist: /var/www/scrape
[Sun Jan 28 11:29:43 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sun Jan 28 11:34:15 2007] [error] [client 127.0.1.1] File does not exist: /var/www/announce
[Sun Jan 28 11:35:31 2007] [error] [client 127.0.1.1] File does not exist: /var/www/scrape
[Sun Jan 28 11:45:31 2007] [error] [client 127.0.1.1] File does not exist: /var/www/scrape
[Sun Jan 28 11:56:03 2007] [error] [client 127.0.1.1] File does not exist: /var/www/scrape
[Sun Jan 28 12:06:04 2007] [error] [client 127.0.1.1] File does not exist: /var/www/scrape
[Sun Jan 28 12:16:04 2007] [error] [client 127.0.1.1] File does not exist: /var/www/scrape
[Sun Jan 28 12:16:59 2007] [error] [client 127.0.1.1] File does not exist: /var/www/announce
[Mon Jan 29 14:08:48 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Tue Jan 30 00:54:36 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Tue Jan 30 20:18:17 2007] [notice] caught SIGTERM, shutting down
[Tue Jan 30 22:01:16 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 16:00:02 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sat Feb 03 16:02:15 2007] [error] [client 127.0.0.1] (13): file permissions deny server access: /var/www/index.html
[Sat Feb 03 16:02:22 2007] [error] [client 127.0.0.1] (13): file permissions deny server access: /var/www/index.html
[Sat Feb 03 16:06:14 2007] [error] [client 127.0.0.1] (13): file permissions deny server access: /var/www/index.html
[Sat Feb 03 16:06:19 2007] [error] [client 127.0.0.1] (13): file permissions deny server access: /var/www/index.html
[Sat Feb 03 16:08:22 2007] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/cgi101.py, referer: http://localhost/
[Sat Feb 03 16:11:40 2007] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/cgi101.py, referer: http://localhost/
[Sat Feb 03 16:11:46 2007] [error] [client 127.0.0.1] (13): file permissions deny server access: /var/www/cgi/cgi.py, referer: http://localhost/
[Sat Feb 03 16:34:17 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 16:34:18 2007] [notice] mod_python: Creating 8 session mutexes based on 20 max processes and 0 max threads.
[Sat Feb 03 16:34:18 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 16:34:26 2007] [error] [client 127.0.0.1] File does not exist: /var/www/cgi, referer: http://localhost/
[Sat Feb 03 16:34:49 2007] [error] [client 127.0.0.1] File does not exist: /var/www/cgi, referer: http://localhost/
[Sat Feb 03 16:34:59 2007] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/cgi.py, referer: http://localhost/
[Sat Feb 03 16:36:00 2007] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/cgi.py, referer: http://localhost/
[Sat Feb 03 16:36:11 2007] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/cgi.py, referer: http://localhost/
[Sat Feb 03 16:40:47 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 16:40:48 2007] [notice] mod_python: Creating 8 session mutexes based on 20 max processes and 0 max threads.
[Sat Feb 03 16:40:48 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 16:40:56 2007] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/cgi.py, referer: http://localhost/
[Sat Feb 03 16:41:00 2007] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/cgi.py, referer: http://localhost/
[Sat Feb 03 16:42:15 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 16:42:39 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 16:42:42 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 16:57:59 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 16:58:02 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 17:00:13 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 17:00:14 2007] [notice] mod_python: Creating 8 session mutexes based on 20 max processes and 0 max threads.
[Sat Feb 03 17:00:14 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 17:00:17 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 17:00:18 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 18:38:52 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 18:38:53 2007] [notice] mod_python: Creating 8 session mutexes based on 20 max processes and 0 max threads.
[Sat Feb 03 18:38:53 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 18:39:48 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here, referer: http://www.ubuntuforums.org/showthread.php?t=91101
[Sat Feb 03 18:44:51 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 18:44:52 2007] [notice] mod_python: Creating 8 session mutexes based on 20 max processes and 0 max threads.
[Sat Feb 03 18:44:52 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 18:49:13 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 18:49:18 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:03:14 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 19:03:15 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 19:03:19 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:03:20 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:03:21 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:03:22 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:04:06 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:04:07 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:04:08 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:04:09 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:04:11 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:11:38 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 19:11:39 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 19:11:44 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:11:45 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:11:46 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 19:12:20 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 19:14:10 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 20:06:00 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 20:06:00 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 20:07:37 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 20:07:38 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 20:07:43 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:09:51 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sat Feb 03 21:10:40 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:10:40 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:11:45 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:11:46 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:11:58 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:11:59 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:11:59 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:12:09 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 21:14:28 2007] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Sat Feb 03 21:17:40 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:41 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:41 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:42 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:42 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:43 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:43 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:44 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:44 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:45 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:17:45 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:18:15 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:19:04 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:19:07 2007] [alert] [client ::1] /var/www/.htaccess: AddType not allowed here
[Sat Feb 03 21:28:54 2007] [notice] caught SIGTERM, shutting down
[Sat Feb 03 21:28:58 2007] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Sat Feb 03 21:29:38 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sun Feb 04 00:24:42 2007] [notice] caught SIGTERM, shutting down
[Sun Feb 04 00:24:43 2007] [notice] mod_python: Creating 8 session mutexes based on 20 max processes and 0 max threads.
[Sun Feb 04 00:24:44 2007] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 configured -- resuming normal operations
[Sun Feb 04 00:24:50 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sun Feb 04 00:24:51 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sun Feb 04 00:24:52 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sun Feb 04 00:24:53 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sun Feb 04 00:27:16 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sun Feb 04 00:27:19 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
[Sun Feb 04 00:27:21 2007] [alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here

```

This seems to be the common problem ```
[alert] [client 127.0.0.1] /var/www/.htaccess: AddType not allowed here
```

---

### Post by jae1227 on 2007-02-04
ok I got it it was a problem in the .htaccess file. It said:

```
AddType text/html .shtml
AddHandler server-parsed .shtml
Options Indexes FollowSymLinks Includes
AddHandler server-parsed .html
AddHandler server-parsed .htm

```

So I got mad and deleted it all. And what do you know, It worked.

---

