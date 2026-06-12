---
title: "Question about Grub"
date: 2007-04-22
forum: General Help
---

### Post by Guns90 on 2007-04-22
Good Morning all;

When Grub boots up and gets to the place where you have to tell it from which OS you want to boot;  ..... has Grub obtained the lists of OS's from just going out and reading them, or does Grub get that information from data provided at the last log off?  Thanks

---

### Post by Martje_001 on 2007-04-22
It's a file GRUB reads. You can edit it by typing in a terminal (where you have installed grub): sudo gedit /boot/grub/menu.lst

---

### Post by Irony on 2007-04-22
Grub reads the following list (which you can look at by double clicking on it);

[PHP]/boot/grub/menu.lst[/PHP]

When you first installed ubuntu grub would also have been installed and told to look at the menu.lst - if you decide to move ubuntu, at some point in the future, to another partition you would have to instruct grub to look at the menu.lst in the new partition or else you would get a grub error.

---

### Post by Irony on 2007-04-22
The correct way to open up graphical programs is;

[PHP]gksudo gedit /boot/grub/menu.lst[/PHP]

Though as it happens sudo gedit works, but don't do say sudo nautilus or else you may end up messing stuff up - use instead gksudo nautilus which will open up nautilus as root.

See;

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Guns90 on 2007-04-22
Thanks guys.  I appreciate it.

---

