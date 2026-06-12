---
title: "How do I get my PHP working with Apache2?"
date: 2007-10-27
forum: General Help
---

### Post by master5o1 on 2007-10-27
I have installed Apache2, PHP5, phpmyadmin & MySQL 5

-- that's, all the "*-common" packages and the ones marked by marking those.

PHP doesn't work and phpmyadmin is not symlinking to /var/www/**phpmyadmin**.

---

### Post by master5o1 on 2007-10-27
Although, it could be just because my httpd.conf file is empty for some unknown reason :S

---

### Post by Matt Yun on 2007-10-27
System configuration options are now in the /etc/apache2/apache2.conf file; you're not supposed to edit it.  Insteand, user customizations go into /etc/apache2/httpd.conf, which is empty by default.

To get PHP working, edit /etc/apache2/httpd.conf and add the following:


```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```

It seems that when you install LAMP scripts in Ubuntu, they all get put in the /usr/share directory.  To get phpmyadmin working, create a symlink in your /var/www directory like so:

```
$ sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

---

### Post by master5o1 on 2007-10-27
still no php :S

maybe i don't have something installed/right

---

### Post by master5o1 on 2007-10-27
php5 refuses to work :( now i can't make my cms :(

---

### Post by louieb on 2007-10-27
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

May want to start over and do it the easy way.
```
sudo tasksel install lamp-server
```That and other good stuff about lamp in the link above. 

Got my home web server up and going using it. [Lou's Home Server Stuff]("http://louieb.isa-geek.net/")

---

### Post by #Reistlehr- on 2007-10-27
A good hint: Never use the packages

Check out XAMPP: [http://apachefriends.org](http://apachefriends.org)
XAMPP is an amazing program. I use it on my local dev servers so i don't have to keep compiling over and over. Don't use it for a live environment (Like host a webserver for the public with it).

---

### Post by louieb on 2007-10-27
> **#Reistlehr- said:**
> Check out XAMPP: [http://apachefriends.org](http://apachefriends.org)

For a local development server +1 for XAMPP
[HOWTO: (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")

---

