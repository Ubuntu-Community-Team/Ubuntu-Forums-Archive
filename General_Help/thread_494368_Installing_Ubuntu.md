---
title: "Installing Ubuntu"
date: 2007-07-06
forum: General Help
---

### Post by tj71587 on 2007-07-06
I have an NVIDIA Geforce 8800 GTS and I cannot get Ubuntu to boot.  I install it through the text based installer and it still wont boot to it.  Does anyone have a suggestion of how to get Ubuntu to work?

---

### Post by confused57 on 2007-07-06
> **tj71587 said:**
> I have an NVIDIA Geforce 8800 GTS and I cannot get Ubuntu to boot.  I install it through the text based installer and it still wont boot to it.  Does anyone have a suggestion of how to get Ubuntu to work?
Here's a thread you might want to read concerning your graphics card:
[http://ubuntuforums.org/showthread.php?t=413961&highlight=Geforce+8800+GTS](http://ubuntuforums.org/showthread.php?t=413961&highlight=Geforce+8800+GTS)

What you can do is try the "vesa" driver to get to a GUI, then it looks like you'll need to install Nvidia drivers from the Nvidia website...when you get the xserver error or corrupted screen, press "Ctrl+Alt+F1", login to the console, enter:
```
sudo /etc/X11/gdm stop
```
make sure to type an uppercase "X" and (one)(one), then enter:
```
sudo dpkg-reconfigure xserver-xorg
```
you can probably just go with the default for most screens, but choose "vesa" for the video driver...once this has completed, enter:
```
startx
```
or if this doesn't work:
```
sudo /etc/init.d/gdm start
```

This might get you to a GUI, then you look into install Nvidia drivers for your card.

---

### Post by tj71587 on 2007-07-06
Thanks...but last time i installed it, it also wiped out my xp partition, do you think it would be safe to try again or would I be better served to use Wubi?

---

### Post by confused57 on 2007-07-06
> **tj71587 said:**
> Thanks...but last time i installed it, it also wiped out my xp partition, do you think it would be safe to try again or would I be better served to use Wubi?
Do you have Ubuntu installed and get a grub menu at boot?  If so, does Ubuntu boot or start to boot?
Maybe someone else can give you a recommendation for Wubi, I've never used it...

---

### Post by establishment on 2007-07-06
Wubi is pretty easy to use if your looking to install Ubuntu but want to keep windows on your computer,
I've been using it and it works pretty well. 
[http://www.wubi-installer.org]("http://www.wubi-installer.org")

---

