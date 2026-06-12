---
title: "Can't get php working with apache 1.3"
date: 2005-10-23
forum: General Help
---

### Post by ManLord on 2005-10-23
I have installed breezy and have installed 

apache
apache-common
libapache-mod-php4
php4
php4-common

I have set my homedir in /etc/apache/httpd.conf to where I want the root (this works)
and I removed the two # for the addtype for php4.

then I did sudo apachectl restart (and later even sudo apachectl stop and then start)

But I can't get apache to process the .php, it just show up in the browser as a file download. 

I did this earlier with a previous installation of breezy. it worked...

Also I had a error when installing some of the packages mentioned over. But have tried to install the packages again without error this time... but it still doesn't work!!!

---

### Post by ronin_ar on 2005-10-23
Have you try to 'complete-remove' the packages and try installing again?
I did setup php5 / apache2  without any problems via synaptic.

---

### Post by ManLord on 2005-10-23
how to complete-remove?
 Actually I would prefer apache 2 and php5, but I just can't seem to change the userdir... Please help me with this also.. I understand userdir is now a module, but when i uncomment the 4 lines in config it still doesn't change. (and have done sudo /etc/init.d/apache2 stop/start)

 When I try to install apache the first time I get this error message (have kubuntu, use adept)
" There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

 And from the console output (translated from norwegian): 
Configuring apache ( 1.3.33-8 ) ... 
dpkg: Error when proccessing apache (--configure):
 the subprocess post-installation script reurned errorcode1
 It occured and error while processing: apache dpkg run finished!

---

### Post by Kushou on 2005-10-31
I got the same problem as you, but today i solve it by doing the following:
Type this command after installed LAMP 
```

a2enmod

```

when prompted, enter the php version you are gonna use, i choose php5.

you may get the following output:
> 
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.


now run this command: 
```
 sudo /etc/init.d/apache2 force-reload

```

it works for me. Good luck.

---

