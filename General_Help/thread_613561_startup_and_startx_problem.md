---
title: "startup and startx problem"
date: 2007-11-15
forum: General Help
---

### Post by kernel1 on 2007-11-15
Hi I have a problem. I have ubuntu 7.04.

The login menu (graphical) suddenly is not starting when I startup Ubuntu. To login I must type startx.

When I start the PC and ubuntu loads it brings me up a terminal. I must login and to type startx. How to recover the auto login graphical menu??

Thanks

---

### Post by Damanther on 2007-11-15
It could be something that got hosed in your xorg.conf file. Save a copy of the file and reconfigure using

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure xserver-xorg

---

