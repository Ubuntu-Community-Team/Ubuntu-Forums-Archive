---
title: "NeoGrub Help?"
date: 2008-01-07
forum: General Help
---

### Post by 2Dum2Kno on 2008-01-07
```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This NeoGrub menu.lst file should be located at \NST\menu.lst of the boot drive.
# Please see the EasyBCD Documentation for information on how to create/modify entries

title Ubuntu
find --set-root /boot/vmlinuz-2.6.17-10-generic
kernel /boot/vmlinuz-2.6.17-10-generic ro root=/dev/sda5
initrd /boot/initrd.img-2.6.17-10-generic
```

i think im doing somthing wrong in NeoGrub Linux
can anyone help

i dont get the --set-root part

---

### Post by Computer Guru on 2008-01-08
the "find --set-root" bit is instead of using "root (hdx,y)" if you don't know it.
 
You need to double-check the /boot/vmlinuz* path and make sure it is correct, as well as update /dev/sda5 to point to the right partition.

---

### Post by 2Dum2Kno on 2008-01-08
could you possibally help me a bit

ive installed it from the partition like this

SDA5 -> part location "/" 
and im sure i all works, i just have never done a bootloader before

---

