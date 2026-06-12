---
title: "owncloud failed installation."
date: 2012-10-24
forum: General Help
---

### Post by odror on 2012-10-24
OS: Ubuntu 12.10 64bit.

I have installed the owncloud package that comes with the dist. (version 4.07debian-1ubuntu1)

After the initial page setup. Instead of going to the next page. I get "access forbidden" message.

The apache error log shows:> [Wed Oct 24 20:45:52 2012] [error] [client 127.0.0.1] Directory index forbidden by Options directive: /usr/share/owncloud/
[Wed Oct 24 20:45:52 2012] [error] [client 127.0.0.1] Directory index forbidden by Options directive: /usr/share/owncloud/, referer: [http://localhost/owncloud/?app=files](http://localhost/owncloud/?app=files)


The .htaccess on /usr/share/owncloud is > ErrorDocument 403 /owncloud/core/templates/403.php
ErrorDocument 404 /owncloud/core/templates/404.php
<IfModule mod_php5.c>
php_value upload_max_filesize 512M
php_value post_max_size 512M
php_value memory_limit 512M
<IfModule env_module>
  SetEnv htaccessWorking true
</IfModule>
</IfModule>
<IfModule mod_rewrite.c>
RewriteEngine on
RewriteRule .* - [env=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteRule ^.well-known/host-meta /public.php?service=host-meta [QSA,L]
RewriteRule ^.well-known/carddav /remote.php/carddav/ [R]
RewriteRule ^.well-known/caldav /remote.php/caldav/ [R]
RewriteRule ^apps/([^/]*)/(.*\.(css|php))$ index.php?app=$1&getfile=$2 [QSA,L]
RewriteRule ^remote/(.*) remote.php [QSA,L]
</IfModule>
Options -Indexes


Is this a bug in the Ubuntu package or my setup is wrong. Is there a ppa with a newer package.

Thanks

---

### Post by Sybrenromer on 2012-11-05
I'm having the same problem.

Have you found a solution yet?
I will post it here if I find it.

---

### Post by odror on 2012-11-05
> **Sybrenromer said:**
> I'm having the same problem.

Have you found a solution yet?
I will post it here if I find it.

No I gave up on it. If you find a solution. Can you please post it.

---

### Post by jonask on 2012-11-25
Hello,
I am on 12.10, 64 bit. I just installed owncloud through the software center. It installed without problems.

However when I tried to configure owncloud in my browser, I got in troubles.

I went to [http://localhost/owncloud/]("http://localhost/owncloud/")

Typed in username and password. Pressed "finish setup":

Then I got message:

can not connect to database, using sqlite3. (unable to find package 'MDB2_Driver_sqlite3' file 'MDB2/Driver/sqlite3.php')

---

### Post by hornetcoach on 2013-01-15
Same issue "can not connect to database, using sqlite3. (unable to find package 'MDB2_Driver_sqlite3' file 'MDB2/Driver/sqlite3.php')"

Anybody find a fix?  I think 12.10 and Owncloud are no bueno.

---

