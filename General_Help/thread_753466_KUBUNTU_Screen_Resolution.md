---
title: "KUBUNTU Screen Resolution"
date: 2008-04-12
forum: General Help
---

### Post by oligray on 2008-04-12
i wanna install kubuntu.....

but the screen resolution is wrong.. it is set at something higher than 1280x800 (the one it should be) on the live cd. 

on ubuntu i could fix this before installation..

but firstly i couldnt get the menu open because it was on the bottom and not viewable.. then i couldnt change it in the settings any way..

will i be able to do this once install or how do i do it..?????

---

### Post by .nedberg on 2008-04-13
Yes, you should be able to fix this with the installed system. In fact it should fix itself when you reboot to the installed system.

Another solution would be to install ubuntu and just install the kubuntu-desktop
```
sudo apt-get install kubuntu-desktop
```
then you can choose Gnome or KDE when you log in. If you like it you can remove ubuntu-desktop with ```
sudo apt-get autoremove ubuntu-desktop
``` but you do not need to do that.

---

