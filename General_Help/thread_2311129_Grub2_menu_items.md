---
title: "Grub2 menu items"
date: 2016-01-24
forum: General Help
---

### Post by Edward_Diener on 2016-01-24
Where do the menu items for grub2 in Ubuntu 15 come from ?

I see items for various OSs on my system as well as for Ubuntu. Are these items generated on-the-fly each time I boot Ubuntu or are they pregenerated somewhere when I install a new kernel ? If they are pregenerated, where are these items stored in the file system ?

---

### Post by yancek on 2016-01-24
They are generated during the installation of the system by Grub.  Also when running sudo update-grub.  The entries are shown in /boot/grub/grub.cfg file which is the menu you see on boot.  There are also files related to Grub in /etc/grub.c and /etc/default/grub.

---

### Post by yancek on 2016-01-24
They are generated during the installation of the system by Grub.  Also when running sudo update-grub.  The entries are shown in /boot/grub/grub.cfg file which is the menu you see on boot.  There are also files related to Grub in /etc/grub.c and /etc/default/grub.

---

### Post by Dennis N on 2016-01-24
You can read more about the grub menu and how it is made here:

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by grahammechanical on 2016-01-24
It is part of the installation process of installing a new Linux kernel that update-grub is run. Actually update-grub is a script. It can be found at /usr/sbin/. It runs a Grub utility called grub-mkconfig that collects information from the other grub configuration files and brings it all together in the grub.cfg file.

Regards.

---

### Post by Edward_Diener on 2016-01-26
Thanks to everyone for pointing out to me where the menu items were located. I did find them in the /boot/grub/grub.cfg script.

---

