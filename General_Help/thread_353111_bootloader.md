---
title: "bootloader"
date: 2007-02-04
forum: General Help
---

### Post by thorosius on 2007-02-04
How can I change the order of the operating systems shown at bootup by bootloader. WindowsXP is shown on the bottom I want it to show at the top. Can anybody help?

---

### Post by moshuptrail on 2007-02-04
The grub menu is located at /boot/grub/menu.lst

It should be easy to figure out. Make a backup copy just in case.

e.g.
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
$ sudo nano /boot/grub/menu.lst

You'll have to move whole sections.

---

