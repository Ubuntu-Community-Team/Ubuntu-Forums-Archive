---
title: "Uninstall"
date: 2007-03-22
forum: General Help
---

### Post by OhioDave on 2007-03-22
How do I completely uninstall ubuntu linux?

---

### Post by taurus on 2007-03-22
Boot from the LiveCD and use gparted (System -> Administration) to either reformat Ubuntu's partition or just delete it.

---

### Post by OhioDave on 2007-03-22
Taurus, will that remove GRUB also?

---

### Post by taurus on 2007-03-22
No, but GRUB won't work anymore since it would look for /boot/grub/menu.lst on Ubuntu's partition.  Therefore, make sure you have Windows CD handy because you need to use it to fix MBR so you can boot Windows again once you remove Ubuntu.

---

