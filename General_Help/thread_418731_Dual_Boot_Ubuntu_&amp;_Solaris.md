---
title: "Dual Boot Ubuntu &amp; Solaris"
date: 2007-04-22
forum: General Help
---

### Post by Arepo on 2007-04-22
I'm trying to dual boot Ubuntu and Solaris, so far I have the Solaris info in Ubuntus menu.lst file, so it looks like this now..

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=698a77b9-5f70-4074-9213-44f4a0f892af ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=698a77b9-5f70-4074-9213-44f4a0f892af ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Solaris 10 11/06 s10x_u3wos_10 X86
root		(hd0,2,a)
kernel		/platform/i86pc/multiboot
module		/platform/i86pc/boot_archive

```

When GRUB loads after I restart, it shows everything alright, but when I try to boot into Solaris, it comes up with "Error 22: No such partition" but I can load Ubuntu fine.

Any help would be great!

---

### Post by BoneKracker on 2007-04-22
I think you have to chainload.  Refer to this article:

[http://www.sun.com/bigadmin/features/articles/grub_boot_solaris.html](http://www.sun.com/bigadmin/features/articles/grub_boot_solaris.html)

---

