---
title: "Switch Grub to use conf files on different partition"
date: 2008-04-20
forum: General Help
---

### Post by SadaraX on 2008-04-20
I have two copies of Linux (MythBuntu) in a system. 
One on /dev/sda1 and the other on /dev/sda2. 
Grub is using the boot-files on /dev/sda2.
I want to switch Grub to use files on /dev/sda1.

I have tried using from the command line:
> 
grub
root (hd0,0)
setup (hd0,0)
quit


There were no errors, but nothing changed. I also tried:
> 
sudo grub-install /dev/sda1


But no change. I have read that Grub does not see the partitions.

Help please?

EDIT: I fixed this. I needed to use: setup (hd0)

---

### Post by sekinto on 2008-04-20
Try this:
grub
root(hd0,0)
setup(hd0)
quit

---

