---
title: "Unable to see external Hard drive?"
date: 2008-05-04
forum: General Help
---

### Post by Watery on 2008-05-04
I've been having problems with my external hdd for a while now, it would randomly decide to unmount itself and corrupt folders.

So, I decided to format it again.
I moved all the files from it to other external hdds and formated it with gparted from ntfs to ext2.

Then I started moving the files back onto it from the other hard drives, but halfway through it just decided to disappear, and now I can't get it back? It dosen't appear on the desktop, but when I type

 ```
sudo fdisk-l
``` 

I can see it here as sdb

```
 Disk /dev/sda: 20.4 GB, 20409532416 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4aef4ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2372    19053058+  83  Linux
/dev/sda2            2373        2481      875542+   5  Extended
/dev/sda5            2373        2481      875511   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000027d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux


```

This is really confusing me, and I would appricate any help anyone can offer.
Thanks.

---

### Post by Watery on 2008-05-04
Just an update, I connected the hard drive to a computer running windows xp, and used a program called Ext2 Volume Manager to view it.

On mounting the hard drive, I found out that it was RAW, not ext2...

I really don't know what happened there?


Edit: I formatted it to ntfs, and tried adding some files to it. The transfer got part way, then there was an error, and the files disappeared from the hard drive? The drive then disappeared, and when I opened it with ext2 volume manager (on the xp computer), again it said it was raw and unformatted??

Thats insane, the hard drive is wiping itself whenever something is transfered? Please, I really need some help now...

---

