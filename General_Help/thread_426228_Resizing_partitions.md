---
title: "Resizing partitions"
date: 2007-04-28
forum: General Help
---

### Post by Steve- on 2007-04-28
I foolishly made my NTFS windows partition too big, so need to shrink that in order to make my ext3 linux partition bigger and perhaps even my swap bigger while I'm at it (so I can hibernate).

I ran the Live CD (with boot option pci=nomsi for my sata HDD), used GParted to shrink my NTFS parition  to 15 GiB.

I now have:

```
/dev/sda1     fat16        86.26 MiB
/dev/sda2     ntfs         15.00 GiB
unallocated                30.80 GiB
/dev/sda3     ext3          9.56 GiB
/dev/sda4     extended    454.97 MiB
 - /dev/sda5  linux-swap  454.97 MiB
```

I want to resize my linux-swap to 2 GiB if possible and give the rest to sda3, but when I select sda3 and go to resize, "Free Space Preceding" is greyed out. Can I not expand sda3 across into that gap?

Thanks
Steve

---

### Post by zvacet on 2007-04-28
I belive that you can move partitions.In horizontal look let unallocated be at the right of /dev/sda3 and than resize.

---

### Post by strabes on 2007-04-28
Are you asking how you should do this? Use a gparted live CD. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You can do everything you asked to do with that CD

---

