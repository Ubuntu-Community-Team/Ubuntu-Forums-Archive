---
title: "broke partition when reinstalling GRUB"
date: 2007-11-01
forum: General Help
---

### Post by frankp_live on 2007-11-01
After windows broke my MBR when scanning the drive, i decided to reinstall GRUB following the [http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett]("HOWTO") HOWTO.
By an accident i wrote > setup (hd1) and not > setup (hd0)
The result is that now GRUB loads up, it gives me the choice of starting Ubuntu, or Windows. Windows works fine, but when i try to load Ubuntu, i get an error message that the partition is invalid or broken.

Is it possible to undo the setup (hd1) command and fix my linux partition, or is my only choice to reinstall Ubuntu

thanks

---

### Post by fdv1 on 2007-11-01
[This will help you]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")

[Alternately, here is how to edit from a Live CD]("http://www.daniweb.com/blogs/entry708.html")

---

### Post by meg23 on 2007-11-01
I have screwed up my mbr so many times partitioning with Ubuntu and Windows. There is a free program called MBRwork you can download to fix your MBR, just google it. Download it to a cd and then restart your computer. At startup it will display the MBRwork interface and you should be able to fix the problem. Its a handy program to have, especially when linux haughtiness takes over and ubuntu punishes you.

---

