---
title: "How to add another boot option to Grub"
date: 2007-12-14
forum: General Help
---

### Post by alexandrum77 on 2007-12-14
Hello,

I've been searching for Grub documentation, but I can't find whether it's possible to add another program or a mounted CD drive as a boot option in the Grub boot menu. For example I’ve added another memtest into the menu.lst..and it works just fine. How or better said what king of image file we can use for Grub to load it. I ask this because I would like to add for instance G4L to it or Partimage or some kind of ghosting option. Here is my menu.lst that works right now with WinXp installed and the other memtest added:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=56567404-457c-47a5-b3db-cae643b7ad2d ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=56567404-457c-47a5-b3db-cae643b7ad2d ro single
initrd		/initrd.img-2.6.22-14-generic

title		Memtest86+v1.70
root		(hd0,6)
kernel		/memtest86+v1.70
quiet

title		Memtest86-v3.2
root		(hd0,6)
kernel		/memtest86v3.2
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional SP2
root		(hd0,0)
savedefault
makeactive
chainloader	+1 

So basically I’ve copied the memtest.bin to /boot and added to the Grub menu. So how can we add for instance G4L to it or Partimage or some other utility program?
What type of images can be loaded with grub and how can we create them.

Thanks,

Alex

---

### Post by Shazaam on 2007-12-14
Everything you wanted to know about grub.....

[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

