---
title: "Help with Grub!!!"
date: 2005-10-16
forum: General Help
---

### Post by jsmidt on 2005-10-16
I was installing a graphical screen for grub and did what gnome-look said by adding a line to my /boo/grub/menu.lst file.  Now grub won't come up when I restart my computer.  Is there any way I can boot into ubuntu still and fix my computer?    Thanks!

---

### Post by afonic on 2005-10-16
You have to boot your PC using a LiveCD or something, mount the partition that contains /boot and then edit /boot/grub/menu.lst to remove that line. That gnome-look might have also created a backup before editing that file so search in the same directory for it.

---

### Post by jsmidt on 2005-10-16
Thanks for the help.  I just have one more basic question, how do you mount a partition?

---

### Post by cbudden on 2005-10-16
Easy way - click system -> Admin -> Disks.  Click on the partitions tab and then click on your partition where /boot is installed.  Then set a mount point (if your in live cd mode then just set it to folder on the desktop).  Then click enable then browse to get to it.

---

### Post by jsmidt on 2005-10-16
Thanks a lot afonic and cubdden.  You saved my computer! :D

---

### Post by jsmidt on 2005-10-16
I just went to my computer and there is no disk menu under administration under system.  Am I looking in the wrong place?  Is it easier to do in a terminal?

---

### Post by cbudden on 2005-10-16
Im not exactly sure as to how you do it in the terminal, but if you run disks-admin from the terminal you get the same as going to system - administration and clicking on Disks.

---

### Post by afonic on 2005-10-16
[QUOTE=jsmidt]I just went to my computer and there is no disk menu under administration under system.  Am I looking in the wrong place?  Is it easier to do in a terminal?[/QUOTE]

You can read [www.ubuntuguide.org](www.ubuntuguide.org) and the Ubuntu wiki. They will answer many of your questions.

---

