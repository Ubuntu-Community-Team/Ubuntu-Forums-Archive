---
title: "Setup Grub to load 2nd partition (windows)"
date: 2007-10-12
forum: General Help
---

### Post by lonrot on 2007-10-12
Hi I'm using Ubuntu x64 7.04, and in the second partition I have Windows xp 32.

What should be the code I need to paste in the grub file?

---

### Post by waawaawee on 2007-10-12
gedit or vi /boot/grub/menu.lst

move the windows part above the ubuntu part. save it and then reboot ur system

---

### Post by lonrot on 2007-10-12
The problem is that Grub does not recognize the 2nd partition, I use super grub loader to run windows, otherwise I cannot access it.

I already tried placing a code to run windows, but at the grub boot it gives me an error and I'm forced to use the super grub cd to get back to windows.

---

