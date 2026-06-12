---
title: "apache2 404 error after upgrade from 13.10 to 14.04 without futher changes"
date: 2014-05-15
forum: General Help
---

### Post by krichter722 on 2014-05-15
Hi together,
after upgrade of Ubuntu (and the default apache2 version), I'm experiencing 404 error with my mediawiki located in /var/www/mediawiki (which worked well before). The setup:


[LIST=1]
[*]/some/folder/var/www is mounted with -o bind,rw under /var/www 
[*]/var/log/apache2/access.log contains nothing but <code>127.0.0.1 - - [15/May/2014:19:16:14 +0200] "GET /mediawiki/ HTTP/1.1" 404 497 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:29.0) Gecko/20100101 Firefox/29.0"</code>, firefox displays 404 error 
[*]<code>$ ls -la /var/www/
ls: Zugriff auf /var/www/dspam nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/dokuwiki nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/joomla nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/.. nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/index.html nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/mediawiki nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/html nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/postfixadmin nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/awffull nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/index.lighttpd.html nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/drupal nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/sarg nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/. nicht möglich: Keine Berechtigung
ls: Zugriff auf /var/www/trac nicht möglich: Keine Berechtigung
insgesamt 0
d????????? ? ? ? ?            ? .
d????????? ? ? ? ?            ? ..
d????????? ? ? ? ?            ? awffull
d????????? ? ? ? ?            ? dokuwiki
d????????? ? ? ? ?            ? drupal
d????????? ? ? ? ?            ? dspam
d????????? ? ? ? ?            ? html
-????????? ? ? ? ?            ? index.html
-????????? ? ? ? ?            ? index.lighttpd.html
d????????? ? ? ? ?            ? joomla
d????????? ? ? ? ?            ? mediawiki
d????????? ? ? ? ?            ? postfixadmin
d????????? ? ? ? ?            ? sarg
d????????? ? ? ? ?            ? trac</code> This occurs rarely and is a problem, but I don't even knows what it means. Otherwise the permissions are the same as in /some/folder/var/www 
[*]ls -la /some/folder/var/www/
insgesamt 44
drwxr-xr-x 11 www-data www-data 4096 Mai  1 11:23 .
drwx------  7 richter  richter  4096 Mär 29 17:34 ..
drw-r--r--  7 www-data www-data 4096 Mär 26 01:36 dokuwiki
drw-r--r--  7 www-data www-data 4096 Mär 26 01:36 dokuwiki.fresh.bk
drw-r--r--  7 www-data www-data 4096 Mär 26 01:28 dokuwiki.old.broken
drw-r--r-- 10 www-data www-data 4096 Sep  4  2013 drupal
drw-r--r-- 18 www-data www-data 4096 Sep 12  2013 joomla
drw-r--r-- 14 www-data www-data 4096 Nov 10  2013 mediawiki
lrwxrwxrwx  1 www-data www-data   19 Mär 15 16:09 postfixadmin -> postfixadmin-2.3.7/
drw-r--r-- 14 www-data www-data 4096 Mär 15 15:42 postfixadmin-2.3.6
drw-r--r-- 15 www-data www-data 4096 Mär 15 16:05 postfixadmin-2.3.7
drw-r--r-- 10 www-data www-data 4096 Sep  4  2013 trac 
[/LIST]

Any help is appreciated!

Best regards,
Kalle

---

### Post by Doug S on 2014-05-15
The default location for DocumentRoot is now /var/www/html
You can change it in /etc/apache2/sites-available/000-default.conf

---

### Post by HiImTye on 2014-05-15
idk if Ubuntu's Apache will be affected by it by default, but Apache changed the format of it's permissions
[http://httpd.apache.org/docs/trunk/upgrading.html](http://httpd.apache.org/docs/trunk/upgrading.html)

---

### Post by ejbiow on 2014-05-20
There is also now a place in /etc/apache2/apache2.conf where you seem to need to change the default Document root.That wasn't the case in some earlier versions.

From 12.04:
$ grep -R '/my/serverlocation' /etc/apache2
/etc/apache2/sites-enabled/000-default: DocumentRoot /my/serverlocation
/etc/apache2/sites-enabled/000-default: <Directory /my/serverlocation>
/etc/apache2/sites-available/default:   DocumentRoot /my/serverlocation
/etc/apache2/sites-available/default:   <Directory /my/serverlocation>

14.04:
$ grep -R '/my/serverlocation' /etc/apache2
/etc/apache2/sites-available/000-default.conf:  DocumentRoot /my/serverlocation  
/etc/apache2/sites-available/default-ssl.conf:DocumentRoot   /my/serverlocation
/etc/apache2/sites-enabled/000-default.conf:    DocumentRoot /my/serverlocation 
/etc/apache2/apache2.conf:<Directory /my/serverlocation>

---

