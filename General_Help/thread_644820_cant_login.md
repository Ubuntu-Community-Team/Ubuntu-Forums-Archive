---
title: "cant login"
date: 2007-12-19
forum: General Help
---

### Post by Ongy on 2007-12-19
i have changed my screen settings cause i was adding another monitor. now i dont get any virtual desktop at all. when i start from grub i get just the console login. i can login, but i stay in the console...

i have already tried to reinstall gdm, kdm, uninstall ubuntu and install ubuntu or xubuntu but anything wouldnt help...

please help, cant acces the system


thenks

---

### Post by metalheart on 2007-12-19
Look into /etc/X11/ directory. Are there more than one file with the name xorg.conf in it (xorg.conf.1 xorg.conf.2 etc)? If there is, copy file with the name xorg.conf to xorg.conf.save and then copy the xorg.conf.X with the largest number 'X' in the name to the xorg.conf. Restart gdm. You need root access to do this.

---

