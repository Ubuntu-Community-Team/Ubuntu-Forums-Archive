---
title: "LAMP on 7.04"
date: 2007-09-08
forum: General Help
---

### Post by opus_az on 2007-09-08
Hi...trying to install LAMP on 7.04. I'm still new to Ubuntu so hopefully I'm not missing something too obvious.

Tried ```
sudo tasksel install lamp-server
``` but that returned aptitude failed (100). 

Then I tried ```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
``` but that returned a whole list of errors.

This is a fresh install of 7.04, with all the latest updates. It's a virtual machine in VMWare Fusion on an OS X MacBook Pro in case that means anything.

Any suggestions? Do I need a server version of Ubuntu?

TIA

---

### Post by opus_az on 2007-09-08
Sorry, nevermind. I got it.
Following these steps [http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu](http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu) and doing individual installs worked for me.

---

