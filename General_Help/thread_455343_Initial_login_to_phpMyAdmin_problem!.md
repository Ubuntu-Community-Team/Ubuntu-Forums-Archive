---
title: "Initial login to phpMyAdmin problem!"
date: 2007-05-26
forum: General Help
---

### Post by JuicedJuice on 2007-05-26
I'm new to linux, installed Ubuntu a couple days ago. Ok, so I used the synaptic package manager to install apache, php, phpMyAdmin and mysql. Everything seems to be installed correctly (everything works) but i'm unsure of how to actually login to phpMyAdmin. I figured i'd create a mysql username/pass through terminal after logging into to mysql as root (GRANT ALL PRIVELEGES ON *.* TO 'admin'@'localhost' ->     IDENTIFIED BY 'password' WITH GRANT OPTION; ) but I can't log into phpMyAdmin after doing so. How the heck do I initially get into phpMyAdmin, how do I create a user/pass for it!? I must be overlooking something simple. Thanks.

Im using ubuntu 7.04 64-bit

---

### Post by JuicedJuice on 2007-05-26
Oh yea, im using phpMyAdmin 2.9.1.1-Debian-2ubuntu1. Maybe someone can lead me in the direction of a good phpMyAdmin forum because using google i've found nothing but hundreds of small crappy forums but nothing official or even anything remoltely helpful in regards to phpmyadmin. Thanks.

---

### Post by ruy_lopez on 2007-05-26
From memory, you have to edit the config.php,ini (or similar name) inside the root phpmysqladmin folder. (Check the apache configuration for where this directory is located. Its either in "/etc/phpmysqladmin", "/usr/share/phpmysqladmin/" or "/var/www/phpmysqladmin".) There is a line in the config.php.ini which tells phpmysqladmin how to login to the mysql server.

---

### Post by JuicedJuice on 2007-05-26
thanks

---

### Post by afonic on 2007-05-26
The default MySQL login after installation is user "root" and a blank password.

You can login with those and then change root's password.

---

### Post by JuicedJuice on 2007-05-26
I thought I had to edit the config.inc.php file in /etc/phpmyadmin and that i'd be good after that, but I discovered out of frustration (by hitting enter over and over several times) that for some reason I can get logged in but only after a few quick consecutive attempts. Then, once I am logged in I get logged out at random! For example sometimes I can get maybe 6-8 clicks worth of work in before I get logged out but other times the first thing I click (and I mean anything I click on the phpmyadmin page) I get logged out. I can then log back in by a few quick consecutive login attempts but only to get logged out at random again and so on and so forth. It's making getting anything done pretty difficult.

---

### Post by Rodrigue on 2007-06-18
Hi,

Have you managed to find your answer yet?
I have the same problem and it's getting frustrating.  

I don't know if it's related but I also have problems starting mysql server at boot time.  It says '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' fails with the following messages

/usr/bin/mysqladmin: connect to server at 'localhost' failed
 /etc/init.d/mysql[6176]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
/etc/init.d/mysql[6176]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

But if I start the server manually after logging in, it works fine.  I read some posts about it, but nothing worked.

If anyone has any idea...

---

### Post by mariuss on 2007-06-18
> **Rodrigue said:**
> Have you managed to find your answer yet?
I have the same problem and it's getting frustrating.

Same here. It started happening right after upgrading from Edgy to Feisty. Not sure if it is the upgrade process or just the new version. Right now I cannot use phpMyAdmin at all.

> I don't know if it's related but I also have problems starting mysql server at boot time.

I don't think so. In my case mysql runs just fine.

Marius

---

### Post by bazzer on 2007-06-19
Same here too. :( Mysql is happy enough, I can log in ok, but the phpmyadmin interface is f l a k y to the point where it boots you after doing just one operation (if you're lucky!)

EDIT: found the solution (for me at least), I have amd64 feisty. Installing md5crypt sorted it.
[http://ubuntuforums.org/showthread.php?t=427228]("http://ubuntuforums.org/showthread.php?t=427228")

---

### Post by Rodrigue on 2007-06-19
You are right, thank you very much bazzer.

Installing php5-mcrypt made it work just fine!

I don't know if I missed something, or they just forgot to mention that phpmyadmin was dependant upon php5-mcrypt.

That's another big problem with simple solution on my long list of such!

---

### Post by PhilOSparta on 2007-06-22
It fixed my problem also.  AMD 64 bit 
This is the specific link:
[http://ubuntuforums.org/showpost.php?p=2680767&postcount=17]("http://ubuntuforums.org/showpost.php?p=2680767&postcount=17")

Thanks for all the work.

Phil

---

