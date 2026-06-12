---
title: "Upgrade to 14.04 from 13.10 broke apache2"
date: 2014-04-18
forum: General Help
---

### Post by f00dl3 on 2014-04-18
For some reason after upgrading to 14.04 from 13.10 the webserver apache2 + php5 no longer works. During the install I did select to retain existing apache2.conf and php ini files - not sure if that may be the reason it doesn't work.

The pages load up - ask me for the password as I have it set up, but when it pulls the page up it says Page not found. The apache2 error logs are clean, and access logs show a 404 error being generated from the pages

I have verified the pages exist, set the /var/www folder to user www-data as owner, and restarted services. I have checked the apache2.conf file - nothing has changed. Live.php exists in /var/www/ASWebUI/res/ .

When accessing the localhost "root" path, it just shows a page with index of / instead of the index.php in the folder.

Error log:

GET /ASWebUI/res/Live.php HTTP/1.1" 404 508 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:28.0) Gecko/20100101 Firefox/28.0

Apache2.conf:

<Directory />
    Options FollowSymLinks
    AllowOverride None
    Require all denied
</Directory>

<Directory /usr/share>
    AllowOverride None
    Require all granted
</Directory>

<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride None
    AuthType Basic
    AuthName "Restricted Access"
    AuthUserFile /var/www/.htpasswd
    Require user **USERNAME**
    Order deny,allow
    deny from all
    allow from 127.0.0.1
</Directory>

Folder listing:

*-EX58-UD4P:~$ ls /var/www
ASWebUI  html  index.php

---

### Post by SeijiSensei on 2014-04-19
Make sure you have **libapache2-mod-php5** installed.

---

### Post by f00dl3 on 2014-04-19
Actually just found the problem. Somehow the upgrade process overwrote or actually created /etc/apache2/sites-enabled/000-default.conf and changed the default WWW path from /var/www to /var/www/html. After editing that file it is now fixed and pointing back to /var/www

---

### Post by SeijiSensei on 2014-04-19
I'm actually pleased to hear that they adopted the RedHat arrangement with the site in /var/www/html.  That way you can create other directories under /var/www that remain outside the DocumentRoot.

---

### Post by Doug S on 2014-04-19
By the way, documenting the change of the default document root from /var/www to /var/www/html missed the deadline for the 14.04 Serverguide. [Bug link]("https://bugs.launchpad.net/serverguide/+bug/1305313").

---

