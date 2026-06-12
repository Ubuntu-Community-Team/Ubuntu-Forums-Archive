---
title: "How to burn dvd.iso on USB drive as startup disk ?"
date: 2021-04-08
forum: General Help
---

### Post by satimis on 2021-04-08
Hi all

I have no optical drive on PC, please advise how to burn dvd.iso on USB drive as startup disk?

$ sudo fdisk -l ```

Disk /dev/sdc: 57.31 GiB, 61530439680 bytes, 120176640 sectors
Disk model:  SanDisk 3.2Gen1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdc1          32 120176639 120176608 57.3G  c W95 FAT32 (LBA)

```

Thanks

Regards

---

### Post by CelticWarrior on 2021-04-08
Any Ubuntu comes with Startup Disk Creator for that purpose.
There are a lot more apps for the same.

---

### Post by TheFu on 2021-04-08
```
sudo cp /path/to/dvd.iso /dev/sdZ
```

Where sdZ is the device file for the USB drive.  When it gets inserted, the dmesg will show that device.  Don't confuse the whole USB device with any partitions on the USB device.  You want the whole device.

For example, on my system, if I insert a flash drive and it says "sdj sdj1 found", then sdj is the whole device and sdj1 is the first partition on the flash drive.  My command would become:
```
sudo cp /tmp/dvd.iso /dev/sdj
```

---

