---
title: "installed software and DE."
date: 2014-04-28
forum: General Help
---

### Post by windowsfree on 2014-04-28
Hello,  I checked before posting and found this to get a list of installed software,[dpkg --get-selections > installed_apps_01.txt], but is there a way of 
showing what desktop enviroments have been installed also.

Thank you,

---

### Post by slickymaster on 2014-04-28
Run the following in a terminal window```
ls -l /usr/share/xsessions/
```

---

### Post by windowsfree on 2014-04-28
Thank you for the quick reply, I will try this later today.

---

### Post by windowsfree on 2014-04-28
how can i remove the gnome.desktop?

---

### Post by slickymaster on 2014-04-29
Please don't forget to do a full back up of your installation before doing it.

[Psychocats pure Xubuntu]("http://www.psychocats.net/ubuntucat/tag/pure-xubuntu/")
[Remove ubuntu-gnome-desktop]("http://askubuntu.com/questions/244654/remove-ubuntu-gnome-desktop")

---

### Post by windowsfree on 2014-04-29
Thanks, I made an image of it using REDO.

---

### Post by slickymaster on 2014-04-29
Xfce and Gnome are "cousins" so you do not want to tear out everything that simply says "gnome", because you have other packages installed that have dependencies currently satisfied by packages provided by Gnome.

---

