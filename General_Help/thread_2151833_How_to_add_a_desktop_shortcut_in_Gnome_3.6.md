---
title: "How to add a desktop shortcut in Gnome 3.6?"
date: 2013-06-05
forum: General Help
---

### Post by Heeter on 2013-06-05
Hi all,

Installed GnomeUbuntu 13.04 64bit and for the life of me, I cannot figure out how to add a shortcut for an application on the desktop. Can someone direct me?

Thanks

Heeter

---

### Post by Isamu715 on 2013-06-06
Run the following in a terminal:
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```
Then you can copy launchers from */usr/share/applications*.

---

### Post by Heeter on 2013-06-07
> **Isamu715 said:**
> Run the following in a terminal:
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```
Then you can copy launchers from */usr/share/applications*.

Awesome, Thank you, Isamu715

That did the trick,

Thanks again.


Heeter

---

