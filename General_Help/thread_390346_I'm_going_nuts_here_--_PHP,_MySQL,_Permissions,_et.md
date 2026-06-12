---
title: "I'm going nuts here -- PHP, MySQL, Permissions, etc.."
date: 2007-03-21
forum: General Help
---

### Post by Singular on 2007-03-21
The Linux guy at my company quit, so me, a starting Ubuntu user, is trying to dig through this thing, and figure out what the heck is wrong with it.

The server has LAMP installed, and it USED to run fine.  Matter of fact, it still 
"displays" fine, but nothing works correctly.

Packages installed under /var/www

Moniwiki
PhpMyAdmin
etc...


So, some symptoms of whats going on:

For the Wiki, you can view it, and try to edit it, but nothing ever commits!

For PhpMyAdmin, it will give you a list of databases on the top left, but if you click on one, nothing happens!

For dotProject which I'm trying to install, it will not use the password/uname that I supply it for installation!  For instance, if I enter the User name and password into the forms it needs for installation, I get 

**No Database Connection available! Access denied for user: 'www-data@localhost' (Using password: NO)  **

Its like any time you enter anything in any form, it fails to use that information, using default information instead.

I checked to see if PHP was in Safe Mode, and it isnt!

What the heck is going on with this thing!

Also, we *had* /var/www on the original harddrive -- then the Linux guy decided to throw it onto a new drive, and thats when I believe everything stopped working.

---

### Post by BIGtrouble77 on 2007-03-23
Di you ever get this working?  I'm having the same issue, but I get this error:
Error
#1045 - Access denied for user 'www-data'@'localhost' (using password: YES)

---

### Post by fyo on 2007-08-14
I have exactly the same problem and have not been able to find a solution. Like the parent poster, I'm GOING NUTS HERE! (also using 64bit feisty)

---

### Post by fyo on 2007-08-14
One way to avoid this is by hard-coding a username and password in the phpmyadmin config file. The ubuntu version of phpmyadmin is a mess, with config files sprayed all over the place in a desperate (and futile) attempt to comply with Debian config location defaults. This causes all sorts of problems (including that the setup script doesn't work properly - or, at least, I can't get it to). It could also easily be this, that is at the root of the problem. 

Anyway, the relevant config file is located here: /etc/phpmyadmin/config.inc.php

Just change auth_type to "config" and type in an appropriate username and password.

---

### Post by cartes on 2007-09-03
OK, this is what you need to do:

1. delete your existing install of phpmysql:
     sudo rmdir /var/www/phpmyadmin
     (I'm assuming that's where you put it)

2. using synaptic package manager, search for phpmyadmin and mark it for installation, then apply and watch it install

3. go to your browser and enter:
     [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
     (this needs to be in lower case, i.e. not ...../phpMyAdmin/)

Job done.

The problem, in my case at least was that I tried to install myself via the phpmyadmin site and the problem is the files there aren't tailored for Ubuntu, whereas the one fetched from package manager is. Slightly older version, yes, but it works fine.

This worked for me, hope it works for you.

Steve

---

### Post by cartes on 2007-09-03
One other thing, your password to get into phpmyadmin will be one of your passwords for mysql, by default user: root and password not set (leave blank).

Steve

---

### Post by thinsoldier on 2007-09-04
I haven't even gotten that far to have such problems....yet.

I'm still trying to figure out why I can't save text files in /var/www/
any ideas?

---

### Post by chris.peplin on 2007-09-06
I just had some luck changing the access type from cookie to http.

---

### Post by doggystyle on 2007-09-15
You need mcrypt to get the password and username right. Now it will just fall back on www-data. 

This will help: 

```
apt-get install php5-mcrypt
```

I think this is a bug within the phpmyadmin apt port. Can someone please be nice and report it? I gotta go.

---

### Post by tvleavitt on 2007-10-16
> **doggystyle said:**
> You need mcrypt to get the password and username right. Now it will just fall back on www-data. 

This will help: 

```
apt-get install php5-mcrypt
```

I think this is a bug within the phpmyadmin apt port. Can someone please be nice and report it? I gotta go.

I think I just ran up against this problem myself. Not sure if installing php5-mcrypt solved it, or I finally just typed the right username and password combo, but I was getting the www-data error message...

---

