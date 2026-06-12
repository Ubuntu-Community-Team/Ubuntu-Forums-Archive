---
title: "How to repair root file system. When fs check does not give any error?"
date: 2008-02-09
forum: General Help
---

### Post by Vaibhav Goyal on 2008-02-09
I have 3 partitions on my SATA hard disk 
/dev/sda1    (Ubuntu 7.10 root)
/dev/sda2    (Swap)
/dev/sda3    (ext3)

I formated /dev/sda3 using gparted in ubuntu 7.10 and NOT the livecd of GParted. 
I rebooted my system and I got an error message. 
..checking root file system
Unable to repair root file system, please repair manually. 

I have tried booting the system using liveCD and running e2fsck on /dev/sda1 and /dev/sda3. But fs check didn't show any errors on my root file system or the sda3.

Please help. :confused:

---

### Post by dcstar on 2008-02-09
> **Vaibhav Goyal said:**
> I have 3 partitions on my SATA hard disk 
/dev/sda1    (Ubuntu 7.10 root)
/dev/sda2    (Swap)
/dev/sda3    (ext3)

I formated /dev/sda3 using gparted in ubuntu 7.10 and NOT the livecd of GParted. 
I rebooted my system and I got an error message. 
..checking root file system
Unable to repair root file system, please repair manually. 

I have tried booting the system using liveCD and running e2fsck on /dev/sda1 and /dev/sda3. But fs check didn't show any errors on my root file system or the sda3.

Please help. :confused:

```
e2fsck -f
```

---

### Post by Ink-Jet on 2008-02-09
UUIDs in /boot/grub/menu.lst and /etc/fstab may not be correct.
Paste both of those files here, please.

---

