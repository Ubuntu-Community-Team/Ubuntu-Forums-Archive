---
title: "Apache problem"
date: 2007-03-25
forum: General Help
---

### Post by sdil on 2007-03-25
Please anyone submit your /etc/apache2 to me by sending to [email]webmaster@zundeyan.zzn.com[/email] . please I hope you all send it.

---

### Post by kidders on 2007-03-25
Is there a competition for the best one? :confused:

---

### Post by jakev383 on 2007-03-25
> **sdil said:**
> Please anyone submit your /etc/apache2 to me by sending to [email]webmaster@zundeyan.zzn.com[/email] . please I hope you all send it.
What exactly are you looking to do?

---

### Post by sdil on 2007-03-26
Do you all want know what the story ? It began with :

My computer can't run phpmyadmin or any script using mysql. I uninstall apache2. After that, I delete the /etc/apache2 and /usr/sbin/apache2. Please anyone send it.:(

---

### Post by kidders on 2007-03-26
It's very, very unlikely that anyone else's **/etc/apache2** will work on your system, unless someone nice goes to the trouble of making you something generic... that you'd only end up having to modify anyway.

As for sending you things out of **/usr/sbin**, you should _never_ ask for such a thing! Blindly copying a binary mailed to you by a stranger onto your computer would be *insane*!

The best advice would be to reinstall Apache from scratch, and start over.

---

### Post by jakev383 on 2007-03-26
> **sdil said:**
> Do you all want know what the story ? It began with :

My computer can't run phpmyadmin or any script using mysql. I uninstall apache2. After that, I delete the /etc/apache2 and /usr/sbin/apache2. Please anyone send it.:(
Let me guess, you deleted the files and now when you try and install it, it dies saying something about the config missing, right? Try this:
sudo dpkg-reconfigure apache2

if that doesn't work:

sudo aptitude reinstall apache2 php4 libapache2-mod-php4

---

### Post by sdil on 2007-03-27
jakev 383, it does not work. Any other ideas ?:confused:

---

### Post by sdil on 2007-03-27
To jakev 383, when I write : sudo dpkg-reconfigure apache2, it not say nothing !

---

### Post by jakev383 on 2007-03-27
> **sdil said:**
> To jakev 383, when I write : sudo dpkg-reconfigure apache2, it not say nothing !
Hmm. That should have worked. Try this:
```
sudo apt-get -y --purge remove apache2 && sudo apt-get -y install apache2
```
You may also try:
```
sudo dpkg-reconfigure apache2-common
```
I think that one covers the missing config files....

---

### Post by sdil on 2007-03-28
Ohh, it is still does not workkk. Any other ideas ?

---

### Post by indytim on 2007-03-28
I just re-read your original posting.  Besides Apache2 (which you've received excellent guidance on), have you, per chance installed MySQL and phpMyAdmin?  Hate to grind down to the basics but....

IndyTim

---

### Post by jakev383 on 2007-03-28
> **sdil said:**
> Ohh, it is still does not workkk. Any other ideas ?
Run the command for apache2-common as well:
```
sudo apt-get -y --purge remove apache2-common && sudo apt-get -y install apache2-common 
```

---

### Post by sdil on 2007-04-05
After I compile the Apache, it get 

no listening sockets available, shutting down
Unable to open logs

When I start. When I stop it, nothing strange.:confused:

---

### Post by sdil on 2007-04-05
Jakev 383, when I write :

sudo apt-get -y --purge remove apache2-common && sudo apt-get -y install apache2-common

It say :

Setting Apache2 to Listen on port 80. If this is not desired, please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.

When I write sudo /etc/init.d/apache3 force load, it says nothing. Other ideas ?

---

### Post by sdil on 2007-04-05
Any other ideas ?

---

### Post by kidders on 2007-04-05
> **sdil said:**
> To jakev 383, when I write : sudo dpkg-reconfigure apache2, it not say nothing !It strikes me that this is probably normal. No message = no error = good ... right? :-?

> **sdil said:**
> After I compile the Apache, it get no listening sockets availableWhy not use the pre-built binaries? Compiling Apache seems like a strange thing to do.

What do your Apache logs say about your latest problem? Does the server start?

---

### Post by garybrlow on 2007-04-05
Compiled Apache and pre-compiled/ repository deb version Apache have different configuration settings. Since you mentioned something about compiling I will assume that you have compiled your own version Apache direct from  [http://httpd.apache.org](http://httpd.apache.org).

All file and subfolders are placed in /usr/local/Apache2/.
All configuration files are located in /usr/local/Apache2/etc.

Compiled version of Apache do not have read/write permissions outside its own folder by default. Logfile writing and other writing operations of certain folder like its own proxy cache etc. including reading permissions for webpages outside its main directory/folder need to have the appropriate user permissions enabled for reading/writing to and from it. Unless of course you put it in your own home directory.

The default log directory in the settings is in /var/log if I'm not mistaken. You have to set the proper permissions.

Cheers!!!


GaryBrlow :biggrin:

---

### Post by sdil on 2007-04-10
When I compile binary package and restart apache using gnome-terminal, it say nothing. Any other ideas ?:confused:

---

### Post by kidders on 2007-04-10
Depending on exactly *how* you're restarting your custom apache install, no output may be exactly what you are supposed to see. Do your system logs indicate any problems? How are you establishing that the web server doesn't actually start?

---

### Post by az on 2007-04-10
> **sdil said:**
> Do you all want know what the story ? It began with :

My computer can't run phpmyadmin or any script using mysql. I uninstall apache2. After that, I delete the /etc/apache2 and /usr/sbin/apache2. Please anyone send it.:(

Probably has nothing to do with apache.  And it's certainly no reason to compile from source.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by garybrlow on 2007-04-10
If you compile Apache manually, you have to manually compile it with PHP module support else you wont be able to run PHP scripts i.e. PHPMyAdmin. Compiled Apache can not use the PHP supplied/installed via repos, you really have to compile PHP as well. Please follow the proper procedure in the documentation it won't work if you take shortcuts and don't read/understand/follow instructions properly. The documentation is found here [http://httpd.apache.org/docs/](http://httpd.apache.org/docs/) and very much cover compilation instructions. By the way Apache 2 has two versions, what version are you using 2.0 or 2.2?

Refer to [www.php.net](www.php.net), the official php manual, or the install.txt that came with the PHP source package for instructions on how to compile apache with php as a module. This covers all version of Apache - 1.3.x, 2.0.x, and 2.2.x.

Cheers!!!


GaryBrlow :biggrin:

---

