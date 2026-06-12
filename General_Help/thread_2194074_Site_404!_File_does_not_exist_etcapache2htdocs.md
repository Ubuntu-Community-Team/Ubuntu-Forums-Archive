---
title: "Site 404! File does not exist: /etc/apache2/htdocs"
date: 2013-12-16
forum: General Help
---

### Post by andy33 on 2013-12-16
Hello there,

After trying to secure PHPmyAdmin through htaccess, my site is compeltely 404.

Here are the error logs:

```
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:37:15 2013] [error] (EAI 2)Name or service not known: Failed to resolve server name for 141.101.116.118 (check DNS) -- or specify an explicit ServerName [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:37:15 2013] [warn] NameVirtualHost *:80 has no VirtualHosts [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:37:15 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.9 with Suhosin-Patch configured -- resuming normal operations [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:37:54 2013] [error] [client 108.162.216.88] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:38:01 2013] [error] [client 82.103.128.63] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:38:02 2013] [error] [client 82.103.128.63] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:38:02 2013] [error] [client 108.162.216.88] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:38:54 2013] [error] [client 188.138.118.184] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:39:07 2013] [notice] caught SIGTERM, shutting down [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:39:08 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.9 with Suhosin-Patch configured -- resuming normal operations [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:39:54 2013] [error] [client 173.245.53.231] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:39:59 2013] [error] [client 108.162.241.143] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:40:02 2013] [error] [client 108.162.242.143] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:40:04 2013] [error] [client 108.162.241.143] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:40:54 2013] [error] [client 76.164.194.74] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:41:54 2013] [error] [client 108.162.241.207] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:42:54 2013] [error] [client 94.46.4.1] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:43:54 2013] [error] [client 50.23.94.74] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:44:54 2013] [error] [client 173.245.49.148] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:45:54 2013] [error] [client 108.162.221.94] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:46:54 2013] [error] [client 82.103.128.63] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:47:54 2013] [error] [client 108.162.216.88] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:48:54 2013] [error] [client 188.138.118.184] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:49:54 2013] [error] [client 173.245.53.231] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:50:54 2013] [error] [client 76.164.194.74] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:51:54 2013] [error] [client 108.162.241.207] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:52:54 2013] [error] [client 94.46.4.1] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:53:54 2013] [error] [client 50.23.94.74] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:54:35 2013] [alert] [client 209.141.185.137] /usr/share/phpmyadmin/.htaccess: Invalid command 'uthType', perhaps misspelled or defined by a module not included in the server configuration [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:54:44 2013] [alert] [client 209.141.185.137] /usr/share/phpmyadmin/.htaccess: Invalid command 'uthType', perhaps misspelled or defined by a module not included in the server configuration [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:54:51 2013] [error] [client 209.141.185.137] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:54:55 2013] [error] [client 173.245.49.148] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:55:54 2013] [error] [client 108.162.221.94] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:56:54 2013] [error] [client 82.103.128.63] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:57:14 2013] [notice] caught SIGTERM, shutting down [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:57:15 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.9 with Suhosin-Patch configured -- resuming normal operations [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:57:54 2013] [error] [client 108.162.216.88] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:58:54 2013] [error] [client 188.138.118.184] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 10:59:54 2013] [error] [client 173.245.53.231] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 11:00:54 2013] [error] [client 76.164.194.74] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 11:01:54 2013] [error] [client 108.162.241.207] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 11:02:02 2013] [error] [client 209.141.185.137] File does not exist: /etc/apache2/htdocs [/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue][Mon Dec 16 11:02:04 2013] [error] [client 209.141.185.137] File does not exist: /etc/apache2/htdocs[/FONT][/COLOR]
```

I am running on a DigitalOcean VPS.

---

### Post by andy33 on 2013-12-16
Somehow my site is redirecting to /etc/apache2/htdocs/, instead of /home/public_html/ now. I have created a temporary htdocs folder so there's no 404 error, but I can't access Webmin, my site or PHPmyAdmin anymore.

---

