---
title: "advice for pc transition"
date: 2007-04-21
forum: General Help
---

### Post by harty83 on 2007-04-21
Hello,

I have a dell optiplex now with feisty on it.  I just got a new machine.  What I want to do is move my old hard drive into the new pc.  My partition table is as follows:

```
alan@desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14202       14593     3148740    5  Extended
/dev/sda2               1        1311    10530576   83  Linux
/dev/sda3            1312       14201   103538925   83  Linux
/dev/sda5           14202       14593     3148708+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

sda2 is my root directory (I'm not for sure why they are not in disk order).  I was hoping to be able to keep my home directory (so I don't have to do a massive backup) and just reinstall feisty onto /dev/sda2 after I move the hard drive to the new machine.  Is this possible? Any advice before I take this adventure?  Should I be aware of anything?  Should I use the alternate install rather than the live?

Thanks!
Alan

---

### Post by Sef on 2007-04-21
> Should I use the alternate install rather than the live?


The alternate cd is less problematic that the Live CD.  The Live CD can have problems with the graphics card that the alternate cd does not.

---

