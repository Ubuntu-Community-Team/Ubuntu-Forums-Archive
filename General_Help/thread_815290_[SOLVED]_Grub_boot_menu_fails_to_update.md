---
title: "[SOLVED] Grub boot menu fails to update"
date: 2008-06-01
forum: General Help
---

### Post by Goldpin on 2008-06-01
I've just installed a kernel and header update to Hardy.  Although the installation script says the /boot/grub/menu.lst file has been updated, the boot menu does not show the new kernel.  Does anyone have an idea of what's going on? :confused:

Thanks in advance.

---

### Post by bwhite82 on 2008-06-01
I've seen many other people report the same problem. I believe it is a bug with 'update-grub'. You can edit your menu.lst by and, just copy and paste the old kernel lines and change the 16 to a 17. Not sure if anyone has filed a bug report yet.

---

