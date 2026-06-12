---
title: "Dual booting vista and ubuntu problem.."
date: 2007-07-26
forum: General Help
---

### Post by Whatever6750 on 2007-07-26
I tried installing ubuntu after a previous vista install and GRUB dident detect vista so now I cannot boot vista. 

I tried adding the entry into GRUB's menu.list but when I select to boot it in GRUB I get error 23 something or other. I'm not totally sure if I had the right hard drive and partition listed in the menu.list entry, sfdisk -l returns this,

```
Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0       -       0          0    0  Empty
/dev/sda2          0+  19456   19457- 156288321    f  W95 Ext'd (LBA)
                end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       3927+   5838    1912-  15358108+  83  Linux
                start: (c,h,s) expected (1023,254,63) found (1022,1,1)
                end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda6       5839+  19456   13618- 109386553+   7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1022,1,1)
                end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda7          0+   3683    3684-  29591635+  83  Linux
/dev/sda8       3684+   3926     243-   1951866   82  Linux swap / Solaris

```

I can't even use the vista DVD to repair vista's MBR and try easyBCD.

Any help to at least get back into vista or get dual booting working would be greatly appreciated.

---

### Post by louieb on 2007-07-26
just wondering what program produced the partition table listing?
why are there 0 length partitions? 
Strange looking partition table. 
Please post the output of **sudo fdisk -l **(lowercase L)
Also what program did you use to partition the disk?

---

### Post by Whatever6750 on 2007-07-26
> **louieb said:**
> just wondering what program produced the partition table listing?
why are there 0 length partitions? 
Strange looking partition table. 
Please post the output of **sudo fdisk -l **(lowercase L)
Also what program did you use to partition the disk?

fdisk -l,
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       19457   156288321    f  W95 Ext'd (LBA)
/dev/sda5            3928        5839    15358108+  83  Linux
/dev/sda6            5840       19457   109386553+   7  HPFS/NTFS
/dev/sda7               1        3684    29591635+  83  Linux
/dev/sda8            3685        3927     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Yeah the drive has had alot of partitioning, Various OS's dual booting linux swap and such with out a full disk format in a long time.

---

### Post by Whatever6750 on 2007-07-27
Oh also I get "error 12 invalid device requested" when trying to boot vista. Ive tryed hd0,0 - hd0,8 with no luck useing,

```
title            Vista
rootnoverify     (hd0,0) 
savedefault
makeactive
chainloader      +1
```

---

### Post by Espreon on 2007-07-27
From what I've heard Vista and GRUB don't work very well with each other. And besides Vista is unworthy of touching any hardware (well IMO of course). If you wanna use Vista, I suggest you installing it in VirtualBox (frig the EULA you paid 4 it and you should install it in or on whatever!).

---

### Post by Whatever6750 on 2007-07-27
> **Espreon said:**
> From what I've heard Vista and GRUB don't work very well with each other. And besides Vista is unworthy of touching any hardware (well IMO of course). If you wanna use Vista, I suggest you installing it in VirtualBox (frig the EULA you paid 4 it and you should install it in or on whatever!).

Even so I still have a vista install that I need for a couple of things and just simply need to be able to boot it.

---

### Post by designwiz on 2007-07-27
e.g. Assumed that /dev/hda1 is the location of Windows partition 

> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst


Append the following lines at the end of file.

> 
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Save the edited file

Finally, do 
> sudo update-grub


Regards Leo J.

---

### Post by Whatever6750 on 2007-07-27
> **designwiz said:**
> e.g. Assumed that /dev/hda1 is the location of Windows partition 



Append the following lines at the end of file.



Save the edited file

Finally, do 


Regards Leo J.

Same "error 12 invalid device requested" deal. I can see the windows partition just find in ubuntu and its mounted at sda6.

---

### Post by louieb on 2007-07-27
According to **fdisk** /dev/sda6 is the only partition  VISTA could be installed in.  Its unusual for a MS OS to be in a logical partition,  with XP and before it is more trouble that its worth. But any way. in GRUB speak sda6 is (hd0,5).

```
title            Vista
rootnoverify     (hd0,5) 
savedefault
makeactive
chainloader      +1
```I see you tried all the different rootnoverify (hd0,#) numbers. and easyBCD. 
Got to go to work now. But a good place to look for a solution is the   [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

Still would like to know what program produced the 1st partition table you posted, it reported some geometry errors. Good luck. Lou.

---

### Post by Whatever6750 on 2007-07-27
> **louieb said:**
> According to **fdisk** /dev/sda6 is the only partition  VISTA could be installed in.  Its unusual for a MS OS to be in a logical partition,  with XP and before it is more trouble that its worth. But any way. in GRUB speak sda6 is (hd0,5).

```
title            Vista
rootnoverify     (hd0,5) 
savedefault
makeactive
chainloader      +1
```I see you tried all the different rootnoverify (hd0,#) numbers. and easyBCD. 
Got to go to work now. But a good place to look for a solution is the   [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

Still would like to know what program produced the 1st partition table you posted, it reported some geometry errors. Good luck. Lou.

That was produced via **sudo sfdisk -l**

---

