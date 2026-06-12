---
title: "Beginner switching to Ubuntu and Apache2 : config help"
date: 2005-05-06
forum: General Help
---

### Post by ciegalo on 2005-05-06
Hi to all,
I'm new both to linux and Apache, coming from win xp and IIS. My goal is to setup a Ubuntu box I'd also use as HTTP & MySQL server.

I've read the guide and installed Apache2, PHP, MySQL. But I don't understand where to customize the default installation, particularly of Apache. On Apache 1.x on win, I had a file where I could set up the document root. I can't find the same lines ? I've also got troubles defining virtual directories as explained in [http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver).

Furthermore, PHPmyAdmin doesn't accept any login from the www browser...

Any pointers woud be greatly apreciated, I'm really looking forward to learning some more and going back to my PHP editing ! Isn't there any GUI to the config files for these tools ?

Thanks in advance !
Ciegalo

---

### Post by blueplazma on 2005-05-06
Welcome to Ubuntu!  The default Apache2 config file in Ubuntu is /etc/apache2/apache2.conf and the default document root is /var/www.  If you need specific help, check out the Server Talk forum.

---

### Post by ciegalo on 2005-05-07
Hi blueplazma,
Thanks for the info, I had found these files without being able to find the doc root. I can't seem to be able to create directories in /var/www (nopermission), so I wanted to set it to /home/myusername/www .
I'll take a look and post in server_talk. 
Thanks for the welcome !
Ciegalo

---

### Post by JC4P on 2005-05-07
[QUOTE=ciegalo]Hi blueplazma,
Thanks for the info, I had found these files without being able to find the doc root. I can't seem to be able to create directories in /var/www (nopermission), so I wanted to set it to /home/myusername/www .
I'll take a look and post in server_talk. 
Thanks for the welcome !
Ciegalo[/QUOTE]
 NOT SECURE! but:
To give yourself permisiion do this...Applications, Sys tools, Root Terminal or Terminal if you cant get in root, and type in sudo passwd root and make up a root password. now go to Computer, System Confg, User Login, Security Tab, and check the box that says ALlow Root to Login (first box from top) then lougout, computer logout, on USER field type in root, and passord type in your password, you know how permission for everything.

---

### Post by ciegalo on 2005-05-10
Hi,
Thanks for the tip... I've been looking for that. 

Yet I guess I'll go to an Apache forum to check out version 1.x vs 2.x. 

Bye !
Ciegalo

---

### Post by shakin on 2005-05-10
As for the document root (and all virtual host stuff), go to /etc/apache2 and list the directory. There are lots of stuff in there.

Each virtual host configuration is in a file in the sites-available/ directory. The default site is just called 'default' and you'll find the document root there. There is a symlink from the sites-enabled/ directory to 'default' in the sites-available/ directory that makes that site enabled. If you copy the sites-available/default file as another file, change the configuration (domain, doc root) and symlink it from sites-enabled/ you'll get another virtual host.

It's a strange way to do the configuration, but I like it much better than Apache's default method. It keeps things much more organized if you have multiple sites running from one server.

---

