---
title: "Apache2 Troubles"
date: 2005-03-26
forum: General Help
---

### Post by s0c0 on 2005-03-26
Hey I've been trying to get apache working the way i'd like to using Ubuntu.  I've never had thi sort of issue w/ other distro's,  but then again I've never user apache 2 before.  When you go to my website [http://apache.liquidcipher.com/](http://apache.liquidcipher.com/) it automatically takes you to the apache2-default directory located in /var/www/ so the web address ends up looking like this: [http://apache.liquidcipher.com/apache2-default/](http://apache.liquidcipher.com/apache2-default/).  There should be a place in the apache2.conf where I can tell it just to look in /var/www and not the default directory.  I cannot find this line anywhere and I cannot find any documentation via google.  Please let me know how to fix this. :confused:

---

### Post by unkwn on 2005-03-26
[QUOTE=s0c0]Hey I've been trying to get apache working the way i'd like to using Ubuntu.  I've never had thi sort of issue w/ other distro's,  but then again I've never user apache 2 before.  When you go to my website [http://apache.liquidcipher.com/](http://apache.liquidcipher.com/) it automatically takes you to the apache2-default directory located in /var/www/ so the web address ends up looking like this: [http://apache.liquidcipher.com/apache2-default/](http://apache.liquidcipher.com/apache2-default/).  There should be a place in the apache2.conf where I can tell it just to look in /var/www and not the default directory.  I cannot find this line anywhere and I cannot find any documentation via google.  Please let me know how to fix this. :confused:[/QUOTE]
 check

/etc/apache2/sites-available

---

### Post by ola on 2005-03-26
The problem/difference from your lasts installs of apache is probably that this version supports vhosts (many hosts on the same IP).

That was my idea about it when I first got in touch with it.. I'll try to post ideas/solutions later.

---

### Post by s0c0 on 2005-03-26
Interesting,  I thought Apache 1.3 supported vhosts.  Anyways I will check the /etc/apache2/sites-available file and see if there is something I can configure.  This is kind of annoying me, so I come up with something tonight.  But let me know if you find an exact solution.

---

### Post by Mr Black on 2005-03-27
I had this same issue when I installed apache2 for the first time.  The way I solved it was to go into the *etc/apache2/sites-enabled* directory and open the *default* file that is located in there.  Then you need to comment out the following line:

[SIZE=2]*RedirectMatch ^/$ /apache2-default/*[/SIZE]

This is what is automaticlly redirecting the webserver to that default apache install page. Also don't forget to open the file via a *sudo* or you won't be able to edit the file, cause it will just open in read only mode.

---

### Post by dataw0lf on 2005-04-19
[QUOTE=s0c0]Interesting,  I thought Apache 1.3 supported vhosts.  Anyways I will check the /etc/apache2/sites-available file and see if there is something I can configure.  This is kind of annoying me, so I come up with something tonight.  But let me know if you find an exact solution.[/QUOTE]
Yes, Apache 1.3 supports vhosts.  Anyone who tells you differently doesn't know what they're talking about.

---

