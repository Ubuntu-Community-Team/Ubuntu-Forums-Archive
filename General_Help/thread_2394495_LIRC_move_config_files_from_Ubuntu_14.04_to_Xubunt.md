---
title: "LIRC move config files from Ubuntu 14.04 to Xubuntu 18.04 - files are different"
date: 2018-06-17
forum: General Help
---

### Post by JimLS on 2018-06-17
In the past when upgrading my mythtv setup I have just moved the files with no issue but the 18.04 install doesn't have a hardware.conf file and apparently the config files have changed a bit.  I was planning to just copy over these files:
lircd.conf
lircmd.conf
hardware.conf
.lircrc from the user directory

I found something about an lirc-old2new script for the pi to convert files but didn't find much detail.  What's the best way to transfer the configuration?

---

### Post by meaje2 on 2018-08-12
Try checking out [https://twosortoftechguys.wordpress.com/2018/07/24/make-lirc-work-in-ubuntu-18-04/](https://twosortoftechguys.wordpress.com/2018/07/24/make-lirc-work-in-ubuntu-18-04/) it involves using lirc .9 from the Ubuntu 16.x series but it seems to work again...  There is also a lirc-setup script that should be used in the install of lirc .10 but for some reason it isn't getting called by dpkg-reconfigure in the Ubuntu 18.04 release.

Good luck,
--Jeff

---

