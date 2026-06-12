---
title: "X does not work"
date: 2007-03-06
forum: General Help
---

### Post by kaiwan on 2007-03-06
Hi! I have installed ubuntu ultimate gamers edition, and after that I have installed legacy drivers for NVIDIA, and now X does not work .... can only log into recovery mode... I wanted to edit NVIDIA driver to VESA in xorg.conf using gedit /etc/X11/xorg.conf but I get an error message to check the gedit help ????

---

### Post by Brunellus on 2007-03-06
> **kaiwan said:**
> Hi! I have installed ubuntu ultimate gamers edition, and after that I have installed legacy drivers for NVIDIA, and now X does not work .... can only log into recovery mode... I wanted to edit NVIDIA driver to VESA in xorg.conf using gedit /etc/X11/xorg.conf but I get an error message to check the gedit help ????
gedit depends on X.  if you have no X, you have no gedit.

before you go hacking up the config files try

sudo dpkg-reconfigure xserver-xorg

and follow the prompts.

---

