---
title: "WD My book duo very slow."
date: 2020-01-19
forum: General Help
---

### Post by saulleg on 2020-01-19
Hi,

I already installed a WD My book duo 4Tb, it is in Raid 0 (2 wd hhd red nas 2tb in one enclosure), but the transfer speed is very slow, it is around 35 mb/s.

It is connected in a USB 3.2 and formatted in EXT4.

Why is this going so slow?

Thanks

---

### Post by TheFu on 2020-01-19
First, have you checked the system logs?

Is the USB port USB3.2 or something else?  Theoretical USB bus speeds are just that - theoretical.  The slowest part in the chain will limit all performance regardless of anything else.   Red WD drives are usually around 125Mbps under ideal situations. These are 5400 rpm disks. For example, my WD Red claims:
```
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 6.0 Gb/s)
```
But in the real world, that becomes ... 
```
$ time dd if=/dev/urandom of=./rand.stuff bs=4M count=1000
1000+0 records in
1000+0 records out
4194304000 bytes (4.2 GB, 3.9 GiB) copied, 304.692 s, **13.8 MB/s**

real    5m4.696s
user    0m0.000s
sys     4m45.848s
```
13.8 MB/s is 110.4 Mbps.  That's in the expected ballpark on a very full disk like mine.  Considering that USB2 has a theoretical bus speed of 480Mbps, the USB isn't the limiting factor. Mine is actually connected via SATA cables, internally.

How is the storage mounted?  **df -Th** + via fstab, manual mount or some other way?
What are the mount options?  **mount**
How are you measuring "transfer speed?"  **cp**, **rsync**, any networking involved, or using some GUI?
What is the source storage and the target storage?  Any non-Linux storage?
Are the partitions aligned?  **parted** will check that.
Is gvfs or gio involved?  If using a GUI, then this is likely.
and finally, how did you create the RAID0?  mdadm, lvm, some other way?

---

### Post by saulleg on 2020-01-20
this harddrive enclosure have a internal raid 0 by default, raid did not create by me, is connected to ubuntu and mounted via fstab.
i tested it in usb2 and usb3 and it is same speed.

Test with My book duo:

```
sudo time dd if=/dev/sdb1 of=./rand.stuff bs=4M count=1000
1000+0 registros leídos
1000+0 registros escritos
4194304000 bytes (4,2 GB, 3,9 GiB) copied, 111,748 s, 37,5 MB/s
0.00user 8.52system 1:51.75elapsed 7%CPU (0avgtext+0avgdata 6644maxresident)k
8098208inputs+8192000outputs (1major+1114minor)pagefaults 0swaps

```


Test with anocher HDD 500gb non raid:

```
 sudo time dd if=/dev/sda1 of=./rand.stuff bs=4M count=1000
1000+0 registros leídos
1000+0 registros escritos
4194304000 bytes (4,2 GB, 3,9 GiB) copied, 40,0747 s, 105 MB/s
0.00user 6.91system 0:40.28elapsed 17%CPU (0avgtext+0avgdata 6640maxresident)k
8146936inputs+8192000outputs (0major+1113minor)pagefaults 0swaps

```

---

### Post by saulleg on 2020-01-21
> **saulleg said:**
> this harddrive enclosure have a internal raid 0 by default, raid did not create by me, is connected to ubuntu and mounted via fstab.
i tested it in usb2 and usb3 and it is same speed.

Test with My book duo:

```
sudo time dd if=/dev/sdb1 of=./rand.stuff bs=4M count=1000
1000+0 registros leídos
1000+0 registros escritos
4194304000 bytes (4,2 GB, 3,9 GiB) copied, 111,748 s, 37,5 MB/s
0.00user 8.52system 1:51.75elapsed 7%CPU (0avgtext+0avgdata 6644maxresident)k
8098208inputs+8192000outputs (1major+1114minor)pagefaults 0swaps

```


Test with anocher HDD 500gb non raid:

```
 sudo time dd if=/dev/sda1 of=./rand.stuff bs=4M count=1000
1000+0 registros leídos
1000+0 registros escritos
4194304000 bytes (4,2 GB, 3,9 GiB) copied, 40,0747 s, 105 MB/s
0.00user 6.91system 0:40.28elapsed 17%CPU (0avgtext+0avgdata 6640maxresident)k
8146936inputs+8192000outputs (0major+1113minor)pagefaults 0swaps

```

I have managed to find the solution. The solution was to connect the cable to a high-amperage USB (they are usually the ones that you put USB SS)
Now the transfer speed is 300MB / s.

---

### Post by TheFu on 2020-01-21
> **saulleg said:**
> I have managed to find the solution. The solution was to connect the cable to a high-amperage USB (they are usually the ones that you put USB SS)
Now the transfer speed is 300MB / s.

Thanks for posting the solution that worked for you. A few questions.
Is the array not externally powered?
Are you certain it is 300 MBps and not 300 Mbps?  Almost no spinning disks cannot reach that speed - very fast enterprise disks only get to 235 MBps.  About 160MBps is the top end for consumer disks.

 The testing didn't appear to use the same commands that I did and cheated by running as root too. I used /dev/urandom to ensure new data was written for each byte, each time. It also ensures that only 1 disk is involved in the writing and no reading is done.  Using /dev/zero should be much, much, faster as should any pure read activity.  Not that my example is golden, but apples-to-apples comparisons are critical.

---

### Post by saulleg on 2020-01-22
> **TheFu said:**
> Thanks for posting the solution that worked for you. A few questions.
Is the array not externally powered?

It is externally powered

> **TheFu said:**
> 
Are you certain it is 300 MBps and not 300 Mbps?  Almost no spinning disks cannot reach that speed - very fast enterprise disks only get to 235 MBps.  About 160MBps is the top end for consumer disks.


Yes it is 300MBps, only one disk normally it is arount 200MBps but my external hdd are 2 disks in raid 0, so it is the speed of one drive is multiplier by two.

---

