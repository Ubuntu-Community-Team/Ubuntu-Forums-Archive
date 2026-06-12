---
title: "how to edit grub.conf in Live CD?? [Resolved]"
date: 2007-01-25
forum: General Help
---

### Post by presbp on 2007-01-25
I have installed grub and ubuntu to my external hard drive.  The external is partitioned because there are backup files on there for Windows.  The drive other than the Ubuntu partition is NTFS.  How do I edit the grub.conf from the live cd now.. I know I have to change it and put chainloader +1 in the grub.conf

thanks

---

### Post by aysiu on 2007-01-25
Are you asking how to mount the drive to edit /boot/grub/menu.lst off the external hard drive?

If it's external, I think you can just turn it on and it should mount. If you need root permissions, press Alt-F2 and type ```
gksudo nautilus
```

---

### Post by presbp on 2007-01-25
no I know how to mount it I just don't know how to start editing the grub.conf

---

### Post by presbp on 2007-01-25
nvm i got it

---

