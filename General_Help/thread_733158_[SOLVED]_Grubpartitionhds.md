---
title: "[SOLVED] Grub/partition/hds ?"
date: 2008-03-23
forum: General Help
---

### Post by teryowen on 2008-03-23
you know how in the grub menu.lst file it uses things like hd0,0 or hd1,2 for the locations of hard drives and partitions.

I was wondering if there is a command to list all the hard drives and partitions with their respective hdX,Y location

so say i have 2 hard drives

160
sda1
sda2

120
sdb1
sdb2

i want something that will tell me

that
sda1 is hd0,0
sda2 is hd0,1

sdb1 is hd1,0
sdb2 is hd1,1

any ideas?

---

### Post by forestpixie on 2008-03-23
cat /boot/grub/device.map

will list the drives - but the partitions I don't know - although you know how they are numbered

---

### Post by teryowen on 2008-03-23
perfect thank you, no more guessing games with multiple drives.

EDIT: Just wondering though if you have say only sda1 and sda5 is the sda1 hd0,0 and the sda5 is hd0,4 or is it hd0,1

---

### Post by forestpixie on 2008-03-23
Absolutely no idea at all :)

---

### Post by louieb on 2008-03-23
> **teryowen said:**
>  Just wondering though if you have say only sda1 and sda5 is the sda1 hd0,0 and the sda5 is hd0,4 or is it hd0,1
Its  (hd0,4) :confused:don't know why -  :)its just the way grub works.

---

### Post by teryowen on 2008-03-23
Alright sweet deal, thanks for all the help.

---

