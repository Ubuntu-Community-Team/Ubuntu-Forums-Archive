---
title: "Can anyone help with this partitioning question, please."
date: 2007-12-21
forum: General Help
---

### Post by L Campbell on 2007-12-21
I have a Gparted Live CD with which I have been trying to set up a partition in a 4GB Pen Drive (aka flash drive, memory stick, etc)

For my application I need at least a 750MB #1 partition. After several tries and also using another 4GB Pen Drive, I have been unable to get Gparted to allow me to have this partition larger than 722MB.

Trying with Fat 16, or Fat 32, doesn't have any effect on the 722MB limit.

Do you have any idea what else I can do?

TIA

---

### Post by forestpixie on 2007-12-21
sorry can't help :( - but why don't you bump your other thread insteaad of starting another one

---

### Post by L Campbell on 2007-12-21
> **forestpixie said:**
> sorry can't help :( - but why don't you bump your other thread insteaad of starting another one

With all due respect here, if you had _read_ my post you would have seen that I did just that.

[http://ubuntuforums.org/showthread.php?t=645645](http://ubuntuforums.org/showthread.php?t=645645)

Kind regards.

---

### Post by beren.olvar on 2007-12-21
Why dont you try fdisk? use:
fdisk /dec/sdb in case sdb is your pendrive (note is sdb not sdb1, you can use 'mount' to see wich device is it)
once in the menu use p to print the partition table, then delete everything you have using d.
after that use w to write and leave. (m for help)

if it doesnt work you may try umounting it first (righ click on the icon in the desktop, then umount or eject)... i am not really sure if it should be umounted or not, but dont think you will lose too much if you try.
if you succed then try using gpart to create new partitions, or even better, try fdisk to do the same :).

hope it works
cheers

---

### Post by forestpixie on 2007-12-21
when I looked it hadn't been for 19 hours

---

