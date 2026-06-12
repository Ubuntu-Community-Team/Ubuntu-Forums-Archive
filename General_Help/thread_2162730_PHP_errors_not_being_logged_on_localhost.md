---
title: "PHP errors not being logged on localhost"
date: 2013-07-15
forum: General Help
---

### Post by neanderslob on 2013-07-15
Hi All,

It seems as though my error log under /var/log/apache2/error.log is not picking up any errors from my local webserver.  I've checked through my php.ini file and it's configured as follows:

```
error_reporting = E_ALL & ~E_DEPRECATED
display_errors = on
display_startup_errors = Off
log_errors = On
log_errors_max_len = 1024
ignore_repeated_errors = Off
ignore_repeated_source = Off
report_memleaks = On
track_errors = on
html_errors = on

```

I'll add in a stray bracket on a php file, bring down the whole site but the error log says nothing.  Other than the following:
> PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Mon Jul 15 00:08:25 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Mon Jul 15 01:44:39 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Mon Jul 15 11:09:31 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Mon Jul 15 14:23:37 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Mon Jul 15 14:23:38 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Mon Jul 15 15:13:47 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Mon Jul 15 15:13:48 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Mon Jul 15 17:26:58 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Mon Jul 15 17:26:59 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Mon Jul 15 17:28:57 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Mon Jul 15 17:28:58 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations


If this might be at all relevant, I've configured the server to use ~/www instead of /var/www.

Thanks in advance for any help on this matter; I'm really scratching my head here.

---

### Post by neanderslob on 2013-07-17
Bump?

---

### Post by Dave_L on 2013-07-17
Wild guesses:

Check that you're looking at the correct php.ini file.  There may be more than one.

Check the Apache configuration file(s), including any .htaccess files, to see if the php.ini settings are being overridden.

If you change php.ini, ensure that you restart Apache.

Try using ini_get() to verify the actual settings.

Try using ini_set() to force logging.

---

