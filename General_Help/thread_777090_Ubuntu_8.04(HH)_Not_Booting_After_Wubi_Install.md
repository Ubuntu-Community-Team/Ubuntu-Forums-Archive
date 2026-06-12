---
title: "Ubuntu 8.04(HH) Not Booting After Wubi Install"
date: 2008-05-01
forum: General Help
---

### Post by NatroXz on 2008-05-01
Hi All,

Having problem booting 8.04 after the instalation is done.
I have no clue what to do.
This is a Wubi instalation in WindowsXP(Just Installed).
WinXP is on C:\
Ubuntu is on D:\

Here is the error mesage :
```
Booting `Ubuntu 8.04, kernel 2.6.24-16-generic
Kernel /boot/vmlinuz-2.6.24-16-generic
root=UUID=5E0484050483DF01 loop=/ubuntu/disks/root.diskrosingle

Error 15 : File not found
Press any key to continue
```

---

### Post by stijngysemans on 2008-05-01
Hey this guy has the same problem!
[http://ubuntuforums.org/showthread.php?t=736469](http://ubuntuforums.org/showthread.php?t=736469)

---

### Post by NatroXz on 2008-05-01
> **stijngysemans said:**
> Hey this guy has the same problem!
[http://ubuntuforums.org/showthread.php?t=736469](http://ubuntuforums.org/showthread.php?t=736469)

Exelent, that did it:popcorn:

The Grub file was pointing to the wrong harddisk.
Changed (hd1,4)to (hd0,4)

Thank You =D>=D>

---

