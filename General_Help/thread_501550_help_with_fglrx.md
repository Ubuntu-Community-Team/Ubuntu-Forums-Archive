---
title: "help with fglrx"
date: 2007-07-15
forum: General Help
---

### Post by bdavies on 2007-07-15
i followed the instructions from this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
(method 2)

when i rebooted my computer i got to the screen where it says ubuntu with the orange bar underneath it and then my screen went blank and nothing happens. what went wrong? does any one know how to fix this? thanks for any help

---

### Post by pedrogl on 2007-07-15
It seems like xserver (or your desktop manager) failed to start. Try switching to a text terminal (CTRL-ALT-F1) and look into the xserver's log:```
less /var/log/Xorg.0.log
```
Also, you can stop gdm (the graphical login screen) and try launching X manually to see what happens:
```
sudo /etc/init.d/gdm stop
startx
```
Please post your findings.

---

