---
title: "Tutorial To Install Wordpress On Local Host Ubuntu 13.04"
date: 2013-09-16
forum: General Help
---

### Post by carmen2012 on 2013-09-16
I'm trying to install Wordpress to run on the local host.  My PC is running Ubuntu 13.04.  I did a Google search on this subject and came across a number tutorials and tried out two of them, but they both failed.

Would someone have some reliable instructions on how to do this?

Thank you

Carmen

---

### Post by mastablasta on 2013-09-16
you need to install lamp first (for example : [http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/) or with single command:

```
sudo apt-get install lamp-server^
```

and then unpack wordpres into /var/www and then follow the wordpress install procedure.: [URL="http://codex.wordpress.org/Installing_WordPress"]http://codex.wordpress.org/Installing_WordPress
[/URL]

if you are still having problmes and if you need it only to develop your site or test it check out turnkey linux: [http://www.turnkeylinux.org/wordpress](http://www.turnkeylinux.org/wordpress)
it's already prepapred image basically debian+wodpress. it only ask you for passwords and such. so you can just download the image file, install virtualbox and just run this server's image in it. then you connect from local browser to the virtual box using the given IP. you can also install it in virtualbox yourself from ISO. it pays to find 32 bit image as they take less ram.

---

### Post by Habitual on 2013-09-16
[The Famous 5-Minute Installation]("http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install")

---

