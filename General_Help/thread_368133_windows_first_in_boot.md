---
title: "windows first in boot"
date: 2007-02-22
forum: General Help
---

### Post by supra104 on 2007-02-22
hi i need to know how to make windows first in the boot menu, and ubuntu second

---

### Post by gozzerd on 2007-02-22
open up the file /boot/grub/menu.lst in gedit and read the directions. You probably are wanting to make windows the default boot option? Best to leave the ubuntu kernels in first place so the menu can be automatically updated when new kernels come out. But making windows the default boot option is easy.

---

### Post by airtonix on 2007-02-22
just remember that the counting of kernels to boot starts from 0.

so default boot option of the windoza partition is say.....the sixth option.
 to boot it without user interaction use '5' as your defaultboot number.

---

