---
title: "Potential hard drive failure?"
date: 2007-03-14
forum: General Help
---

### Post by Mystrick on 2007-03-14
I may be experiencing a hard drive failure, but want to get some feedback from the experts here.  This is the situation:

My slave for IDE1 stopped working last night.  It is a 200 GB drive with a single ext3 partition that is used to store media files, and is accessed by /dev/hdd1.  After a power failure last night I rebooted and now can not access it.  The block devices for it failed to appear upon reboot (I still have /dev/hdc -- my DVD drive -- and can access that just fine though, so I doubt it was a failure of the secondary IDE controller or the cable).  I rebuilt the block devices using the following commands:

```

sudo mknod /dev/hdd b 22 64
sudo mknod /dev/hdd1 b 22 65
sudo chmod 0660 /dev/hdd
sudo chmod 0660 /dev/hdd1
```

Still no joy.  Checking my dmesg log with the following command:

```

cat /var/log/dmesg | grep hdd
```

only gives the following:

```

ide1:  BM-DMA at 0xfd08-0xfd0f, BIOS settings: hdc:DMA, hdd:DMA
```

as opposed to the output of this:

```

cat /var/log/dmesg | grep hdc
```

which gives the following:

```

       ide1:  BM-DMA at 0xfd08-0xfd0f, BIOS settings: hdc:DMA, hdd:DMA
hdc:  TSSTcorpCD/DVDW TS-H552L, ATAPI CD/DVD-ROM drive
 hdb:<6>hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
```

Output of:

```

sudo fdisk -l
```

is:

```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5131    41214726   83  Linux
/dev/hda2            5132        7681    20482875   83  Linux
/dev/hda3           19197       19457     2096482+  82  Linux swap / Solaris
/dev/hda4            7682       19196    92494237+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14593   117218241   83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux
```

Does anyone have any thoughts as to what may be causing this aside from a drive failure, or any other ideas for what to try?  I'd appreciate any help that anyone can give.  Thanks!

- Mystrick -

---

