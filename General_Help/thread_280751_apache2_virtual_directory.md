---
title: "apache2 virtual directory"
date: 2006-10-19
forum: General Help
---

### Post by tr3s on 2006-10-19
hi! how do i create a virtual directory in apache2 (just like in IIS)?

already tried by putting 

```
Alias /tr3s/ "/home/tr3s/web/"
    <Directory "/home/tr3s/web/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
```

in /etc/apache2/sites-available/default

is this correct?

but when i tried to access the directory, the browser displayed a 403 forbidden error. i also already issued the command

```
chmod 755 /home/tr3s/web/
```

tnx

---

### Post by tr3s on 2006-10-30
ok. the alias block should be placed in /etc/apache2/conf.d/alias (from [How to map URLs to folders outside /var/www/]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F")).

is this a directory permission issue or i am still missing something in apache configuration?

btw, i already tried different permissions on the /home/tr3s/web/ folder.

still there's the permission error.

---

### Post by blind0wl on 2006-10-30
Post your /var/log/apache/access.log

Might be worth doing

```
tail -50 /var/log/apache/access.log
```

Blindy

---

### Post by tr3s on 2006-10-30
here's from the /var/log/apache2/access.log

```
127.0.0.1 - - [30/Oct/2006:08:24:25 +0800] "GET /?client=SNOW&version=4.10.9&hostfile=1 HTTP/1.1" 200 580 "-" "FrostWire/4.10.9"
127.0.0.1 - - [30/Oct/2006:08:27:34 +0800] "GET /?client=SNOW&version=4.10.9&hostfile=1 HTTP/1.1" 200 580 "-" "FrostWire/4.10.9"
127.0.0.1 - - [30/Oct/2006:08:37:23 +0800] "GET /?client=SNOW&version=4.10.9&hostfile=1 HTTP/1.1" 200 580 "-" "FrostWire/4.10.9"
127.0.0.1 - - [30/Oct/2006:09:04:33 +0800] "GET /tr3s/ HTTP/1.1" 403 411 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7"
127.0.0.1 - - [30/Oct/2006:09:04:33 +0800] "GET /favicon.ico HTTP/1.1" 404 294 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7"
127.0.0.1 - - [30/Oct/2006:09:05:39 +0800] "GET /favicon.ico HTTP/1.1" 404 294 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7"
127.0.0.1 - - [30/Oct/2006:18:20:38 +0800] "GET /tr3s/ HTTP/1.1" 403 411 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7"
127.0.0.1 - - [30/Oct/2006:18:20:39 +0800] "GET /favicon.ico HTTP/1.1" 404 294 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7"

```

here's from /var/log/apache2/error.log

```
[Mon Oct 30 08:20:01 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Mon Oct 30 09:04:33 2006] [error] [client 127.0.0.1] (13)Permission denied: access to /tr3s/ denied
[Mon Oct 30 09:04:33 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Oct 30 09:05:39 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Oct 30 18:20:38 2006] [error] [client 127.0.0.1] (13)Permission denied: access to /tr3s/ denied
[Mon Oct 30 18:20:39 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

```

---

### Post by blind0wl on 2006-10-30
OK, check your ownership of the folder, apache needs to be owner of /home/tr3s/web/

chown -R www-data:www-data /home/tr3s/web

or whatever group your apache is being run by

---

### Post by tr3s on 2006-10-30
already issued ```
chown -R www-data:www-data /home/tr3s/web
```. www-data is the user and group of apache2. same output in error.log and access.log, cant get through

---

### Post by tr3s on 2006-10-30
btw, the user and group in apache2.conf is set to www-data but i cant find that user or group in the users/groups list. how bout that?

---

### Post by blind0wl on 2006-10-30
As long as the www-data is running apache in ps -aux, you should be ok.  You've obviously restarted apache since the alias directive?

---

### Post by blind0wl on 2006-10-30
Maybe also try removing the speech marks from the Alias line.

So

```
Alias /tr3s/ /home/tr3s/web/
    <Directory /home/tr3s/web/>
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
```

---

