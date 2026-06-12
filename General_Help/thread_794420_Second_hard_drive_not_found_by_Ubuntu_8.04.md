---
title: "Second hard drive not found by Ubuntu 8.04"
date: 2008-05-14
forum: General Help
---

### Post by Zyndrof on 2008-05-14
Hi!

I'm proud to say I'm finally using Ubuntu 8.04 after half a week of stubbornly trying to install the OS on my system. I notice one problem though. Ubuntu doesn't show my second hard drive containing all my important files and documents. I don't even know how to specify my question further than, how can I possibly solve this?

Thank you for your time!
Zyndrof

---

### Post by AlanR8 on 2008-05-14
Is the second drive recognised in the BIOS?

I just made a "server" running Kubuntu 8.04 and have the OS on a 13 gig disk. I went out and bought a 500 gig drive for data etc.

It was recognised in the BIOS but was not visible to the OS. I installed Gparted, a partitioning piece of software, and it was visible there. I formatted the disk and all was well.

---

### Post by geo909 on 2008-05-14
> **Zyndrof said:**
> Hi!

I'm proud to say I'm finally using Ubuntu 8.04 after half a week of stubbornly trying to install the OS on my system. I notice one problem though. Ubuntu doesn't show my second hard drive containing all my important files and documents. I don't even know how to specify my question further than, how can I possibly solve this?

Thank you for your time!
Zyndrof

Try

```
sudo fdisk -l
```

Can you see your drive there?
If you do, it's just not mounted.
Try 
```

sudo mkdir /media/mydisk
sudo mount /dev/yourdisk /media/mydisk
```

Sorry if I say things too obvious for you, 
but I don't know how familiar you are with linux.

---

### Post by Zyndrof on 2008-05-15
Is there a risk involved? I mean, can I lose the data on my hard drive? It is very important that I don't since it contains all my back up files.

Oh, and I'm a almost complete beginner in Linux.

---

### Post by Zyndrof on 2008-05-15
I tried 
```
sudo fdisk -l
```
and it seemed to find only one disk
```
Disk /dev/sda: 160,0 GB, 160041885696 byte
255 heads, 63 sectors/tracks, 19457 cylinders
Units = cylinders of 16065 · 512 = 8225280 byte
Disk identifier: 0x1549f232

    Unit  Start     Beginning   End     Block       Id  System
/dev/sda1   *           1       18890   151733893+  83  Linux
/dev/sda2           18891       19457     4554427+   5  Expanded
/dev/sda5           18891       19457     4554396   82  Linux alternation / Solaris
```

If it looks weird to you it's because I translated it from Swedish.

I just checked the BIOS and it doesn't recognize the second hard drive. Just the first and primary one. I don't know if it matters but the hard drives are both of the same brand, size and ID.

Thank you for your time.

---

### Post by geo909 on 2008-05-15
> **Zyndrof said:**
> I tried 
```
sudo fdisk -l
```
and it seemed to find only one disk
```
Disk /dev/sda: 160,0 GB, 160041885696 byte
255 heads, 63 sectors/tracks, 19457 cylinders
Units = cylinders of 16065 · 512 = 8225280 byte
Disk identifier: 0x1549f232

    Unit  Start     Beginning   End     Block       Id  System
/dev/sda1   *           1       18890   151733893+  83  Linux
/dev/sda2           18891       19457     4554427+   5  Expanded
/dev/sda5           18891       19457     4554396   82  Linux alternation / Solaris
```

If it looks weird to you it's because I translated it from Swedish.

I just checked the BIOS and it doesn't recognize the second hard drive. Just the first and primary one. I don't know if it matters but the hard drives are both of the same brand, size and ID.

Thank you for your time.

 Hello, 

yes, there's no second drive recognized there, but that's expected if BIOS cannot see it. I am afraid I can't help when it comes to BIOS and/or hardware, sorry...
Anybody else?

---

