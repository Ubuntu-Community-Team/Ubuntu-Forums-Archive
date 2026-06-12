---
title: "Recovering data from SD card (and mounting it)"
date: 2008-01-12
forum: General Help
---

### Post by kung fu buntu on 2008-01-12
The SD card for my camera has apparently suffered some data corruption on the filesystem metadata.

When the camera is turned on it asks to format the card.
When the card is plugged on my Linux system says:```
SCSI device sdc: 125952 512-byte hdwr sectors (64 MB)
sdc: Write Protect is off
sdc: Mode Sense: 17 00 00 08
sdc: assuming drive cache: write through
 sdc: unknown partition table
```

I was able to read the card with:```
ddrescue  -v -r 5 /dev/sdc /vault/sdcard.dd sdcard_read.log
```No errors were reported.

Now, when I try to mount the image with:
**mount -o loop /vault/sdcard.dd /mnt/disk/** the result is: ```
mount: you must specify the filesystem type
```
If I try to mount it with:
**mount -t vfat -o loop /vault/sdcard.dd /mnt/disk/** the result is:```
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` and dmesg says:> FAT: invalid media value (0x08 )
VFS: Can't find a valid FAT filesystem on dev loop1.

Any way of recovering those photos?
Thanks!

---

### Post by erpo on 2008-01-13
First of all, any time you need to recover data there is a chance that it cannot be done. Sometimes you can pay a professional for better chances at recovering data, but that can be very expensive. Think about your backup strategy. Do not keep the only copy of your important photos on SD cards.

Your problem is that the partition table has been wiped out, probably because it got overwritten accidentally by your computer. It is also possible that your camera firmware went nuts and nuked the partition table, but IMHO that is unlikely. You can see this by reading the first error message.

You are misusing ddrescue. That command is useful when the device you're trying to mount is physically broken and gives hardware read errors. You want to mount a partition, but what you're getting is a copy of the entire disk.

If your SD card's partition table was set up in the most common way (one FAT32 partition as large as possible), you may be able to extract the partition by skipping the first sector and dd'ing everything after it.

```

sudo dd if=/dev/sdc of=test1.dd bs=512b skip=1
sudo mount -o loop -t vfat test1.dd /mnt/disk

```

---

