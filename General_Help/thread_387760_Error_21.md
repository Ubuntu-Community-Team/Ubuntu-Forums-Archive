---
title: "Error 21"
date: 2007-03-18
forum: General Help
---

### Post by flapjack23 on 2007-03-18
I have recently installed ubuntu-server 6.10 on an old compaq. (think pentium 3 old). I succesfully installed server, and when I went to boot, the first line of grub loaded, and then the next line read "Error 21" I tried reinstalling multiple times. I know the prolem isn't my cd, because it works in VMware.

Does anyone know how I can fix this problem?

---

### Post by Cannonade on 2007-03-18
Error 21 is when it thinks the drive doesn't exist.

This could be because your grub file is not set up correctly. Could you try using the Super Grub Disc to get into ubuntu and check how the root in menu.lst compares with the device map. It maybe that grub is trying to detect Linux on the wrong root.

I may be mixing this up with a different problem, but it's all I can think of.

---

### Post by flapjack23 on 2007-03-19
It appears the problem is very deep. I cant even boot from the Super Grub Disk, I cant install grub again, or do anything with the grub disk.

---

### Post by flapjack23 on 2007-03-19
i switched the ide cables on my motherboard, and i finnally booted of of the super grub disk. I think it works now :)

---

