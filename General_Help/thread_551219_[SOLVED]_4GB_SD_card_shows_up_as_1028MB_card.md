---
title: "[SOLVED] 4GB SD card shows up as 1028MB card?"
date: 2007-09-14
forum: General Help
---

### Post by krandun on 2007-09-14
I have a 4GB card that I'm trying to format to hold all my MP3s (player doesn't support .ogg, darn it). FDISK, Nautilus, and PCman FM all treat the card as if it only holds 1 GB or so (PCman shows the card as being 3.8GB, but it only allows me to copy about 980MB to it before it fills up).

Looking at other threads, I read about the FAT32 limit on files in the root folder, so I've made a subfolder to put my music. It still fills up way too fast.

Basically my question is: what am I doing wrong? The card works fine in Windows, I also have two 2GB cards that have the same problem (Though they're 1003MB in Fdisk).

Edit: Turns out my card reader didn't support cards that large.

---

### Post by peabody on 2007-09-14
So you've been able to format the card and have it store more than 1 gig of memory in windows?  It may be a problem with Linux's FAT32 support.  Have you tried ext2 or 3?  From what I understand, there are free implementations of read/write support for ext2/3 in Windows.

---

### Post by psusi on 2007-09-14
What does fdisk -l show?

---

### Post by krandun on 2007-09-14
I had not tried EXT2 or 3, but I just made it an EXT2 volume. Still no dice. It's not the filesystem, it's something about how the full disk volume is read, since FDISK is having the same problem.
Also, I doubt my MP3 player will read an EXT2 filesystem.

I just formatted it in Windows to FAT, here's the mount output:
> /dev/sdb1 on /media/NEW VOLUME type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


Here's Fdisk's p command:
> Disk /dev/sdb1: 4112 MB, 4112607744 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   ?       48437      119493   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(48436, 183, 40)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(119492, 104, 7)
Partition 1 does not end on cylinder boundary.
/dev/sdb1p2   ?       10501      131013   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(10500, 111, 30)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(131012, 158, 28)
Partition 2 does not end on cylinder boundary.
/dev/sdb1p3   ?      116395      236907   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(116394, 188, 12)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(236906, 234, 25)
Partition 3 does not end on cylinder boundary.
/dev/sdb1p4   ?           1      226407  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(226406, 223, 57)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


Wonder how that happened. Anyway, now I can use the whole thing... But I'd still like to be able to work with it in Linux.

---

### Post by psusi on 2007-09-15
Looks like it is formatted without partitions, so just drop the 1 from the device name to mount the entire disk.

---

### Post by krandun on 2007-09-15
.. As soon as I posted that, I checked fdisk -l.

> Disk /dev/sdb: 1028 MB, 1028653056 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         500     4016218+   6  FAT16


It SAYS 1028 MB, but it's still letting me write to the whole thing... Next I'm going to try formatting it again. Just in case.

---

### Post by psusi on 2007-09-15
Why do the two fdisks disagree?  What changed?

---

### Post by krandun on 2007-09-15
I copied some MP3s to the root folder, ran out of file locations, deleted one MP3, created a folder, tried to rename it (failed, I forget the error), copied some more MP3s to the new folder (that's how I know it was holding more stuff), deleted all the MP3s and the folder from the root folder, and now I'm in the process of copying around 4GB of MP3s to the card.
Stopped the copying.

Now Fdisk says:
> Disk /dev/sdb: 1028 MB, 1028653056 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         500     4016218+   6  FAT16

Same as the last time. Now re-formatting it....
After deleting the partition Windows created, fdisk says:
> Disk /dev/sdb: 1028 MB, 1028653056 bytes
32 heads, 62 sectors/track, 1012 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
which is back to what it was when I made the first post, 1028MB drive, about 900MB usable.

---

### Post by psusi on 2007-09-15
I am confused because your first post showed that windows did not use partitions at all.  The device had no partition table.

---

### Post by krandun on 2007-09-15
The one at the top, with all the partition outputs? Post #4 in this thread? I know it had at least 1 partition, because Windows won't let me format an empty device. I usually do that in Linux though, since Windows doesn't recognize more than 1 partition anyway.

---

### Post by krandun on 2007-09-15
Okay, I just started trying to dd the disk. Every time, I get a 1GB image. This time, I ran dd, then started copying MP3s after dd finished. I've put 3GB on already and it's still running. So apparently dd is another one of those programs that I'm not using properly.

---

### Post by psusi on 2007-09-15
What was the exact command you used?

---

### Post by krandun on 2007-09-15
> sudo fdisk /dev/sdb
mkdosfs -I -F 32 -n Music /dev/sdb
dd if=/dev/sdb of=~/Desktop/fourgig.dd

One thing that occured to me this morning, one time when I tried formatting the partition in Windows I selected 512 byte sectors (instead of letting format pick the sector size) and got an error that said 512 was too small for this media. I notice that fdisk is showing 512 byte sectors in every one of the outputs I've posted so far.
I just formatted it in Windows again, and picked 1024 byte sectors. Fdisk is still showing the card as 1GB, 512 byte sectors.

Thank you for trying to help me, I'm sorry I'm confusing you.

---

### Post by psusi on 2007-09-15
Sectors are always 512 bytes.  FAT uses clusters, which can be an even power of 2 number of sectors.  Best to let it pick the size; using smaller clusters wastes more space.  What was the size of that output file from dd?  Can you post the output of dmesg?

---

### Post by krandun on 2007-09-15
I saved dd files twice, once when I could only access 1GB and once when I could write to the full 4GB. Both of the images are 1028653056 (bytes? Output of ls -l). 

The output of dmesg after I put the card in was 1628 lines. I can send you the whole thing if you think that will help, but here's a few lines from the start and end.

> [  369.140000] usb 4-5: new high speed USB device using ehci_hcd and address 3
[  369.272000] usb 4-5: configuration #1 chosen from 1 choice
[  369.524000] usbcore: registered new interface driver libusual
[  369.544000] Initializing USB Mass Storage driver...
[  369.544000] scsi0 : SCSI emulation for USB Mass Storage devices
[  369.544000] usbcore: registered new interface driver usb-storage
[  369.544000] USB Mass Storage support registered.
[  369.544000] usb-storage: device found at 3
[  369.544000] usb-storage: waiting for device to settle before scanning
[  374.544000] usb-storage: device scan complete
[  374.544000] scsi 0:0:0:0: Direct-Access     GENERIC  USB Storage-CFC  010D PQ: 0 ANSI: 0 CCS
[  374.544000] scsi 0:0:0:1: Direct-Access     GENERIC  USB Storage-MMC  010D PQ: 0 ANSI: 0 CCS
[  374.544000] scsi 0:0:0:2: Direct-Access     GENERIC  USB Storage-MSC  010D PQ: 0 ANSI: 0 CCS
[  374.664000] sd 0:0:0:0: Attached scsi removable disk sda
[  374.668000] SCSI device sdb: 2009088 512-byte hdwr sectors (1029 MB)
[  374.668000] sdb: Write Protect is off
[  374.668000] sdb: Mode Sense: 00 00 00 00
[  374.668000] sdb: assuming drive cache: write through
[  374.672000] SCSI device sdb: 2009088 512-byte hdwr sectors (1029 MB)
[  374.676000] sdb: Write Protect is off
[  374.676000] sdb: Mode Sense: 00 00 00 00
[  374.676000] sdb: assuming drive cache: write through
[  374.676000]  sdb: unknown partition table
[  374.680000] sd 0:0:0:1: Attached scsi removable disk sdb
[  374.684000] sd 0:0:0:2: Attached scsi removable disk sdc
[  374.712000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  374.716000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[  374.716000] sd 0:0:0:2: Attached scsi generic sg2 type 0
[  375.892000] attempt to access beyond end of device
[  375.892000] sdb: rw=2, want=7821081, limit=2009088
[  375.892000] attempt to access beyond end of device
[  375.892000] sdb: rw=2, want=7821082, limit=2009088
[  375.892000] attempt to access beyond end of device
[  375.892000] sdb: rw=2, want=7821083, limit=2009088
[  375.892000] attempt to access beyond end of device
[  375.892000] sdb: rw=2, want=7821084, limit=2009088
[  375.896000] attempt to access beyond end of device
[  375.896000] sdb: rw=2, want=7821085, limit=2009088
[  375.896000] attempt to access beyond end of device
[  375.896000] sdb: rw=2, want=7821086, limit=2009088
[  375.896000] attempt to access beyond end of device
[  375.896000] sdb: rw=2, want=7821087, limit=2009088
[  375.896000] attempt to access beyond end of device
[  375.896000] sdb: rw=2, want=7821088, limit=2009088
[  375.896000] attempt to access beyond end of device
[  375.896000] sdb: rw=0, want=7821081, limit=2009088
[  375.896000] FAT: Directory bread(block 7821080) failed
[  375.896000] attempt to access beyond end of device
[  375.896000] sdb: rw=0, want=7821082, limit=2009088
[  375.896000] FAT: Directory bread(block 7821081) failed
[  375.900000] attempt to access beyond end of device
[  375.900000] sdb: rw=0, want=7821083, limit=2009088
[  375.900000] FAT: Directory bread(block 7821082) failed
[  375.900000] attempt to access beyond end of device
[  375.900000] sdb: rw=0, want=7821084, limit=2009088
[  375.900000] FAT: Directory bread(block 7821083) failed
[  375.900000] attempt to access beyond end of device
[  375.900000] sdb: rw=0, want=7821085, limit=2009088
[  375.900000] FAT: Directory bread(block 7821084) failed
[  375.900000] attempt to access beyond end of device
[  375.900000] sdb: rw=0, want=7821086, limit=2009088
[  375.900000] FAT: Directory bread(block 7821085) failed
[  375.900000] attempt to access beyond end of device
[  375.900000] sdb: rw=0, want=7821087, limit=2009088
[  375.904000] FAT: Directory bread(block 7821086) failed
[  375.904000] attempt to access beyond end of device
[  375.904000] sdb: rw=0, want=7821088, limit=2009088
[  375.904000] FAT: Directory bread(block 7821087) failed
[  375.904000] attempt to access beyond end of device
[  375.904000] sdb: rw=2, want=7821089, limit=2009088
[  375.904000] attempt to access beyond end of device
[  375.904000] sdb: rw=2, want=7821090, limit=2009088
[  375.904000] attempt to access beyond end of device
[  375.904000] sdb: rw=2, want=7821091, limit=2009088

...

[  376.064000] attempt to access beyond end of device
[  376.064000] sdb: rw=0, want=7821153, limit=2009088
[  376.064000] FAT: Directory bread(block 7821152) failed
[  376.064000] attempt to access beyond end of device
[  376.064000] sdb: rw=0, want=7821154, limit=2009088
[  376.064000] FAT: Directory bread(block 7821153) failed
[  376.064000] attempt to access beyond end of device
[  376.064000] sdb: rw=0, want=7821155, limit=2009088
[  376.064000] FAT: Directory bread(block 7821154) failed
[  376.064000] attempt to access beyond end of device
[  376.064000] sdb: rw=0, want=7821156, limit=2009088
[  376.064000] FAT: Directory bread(block 7821155) failed
[  376.064000] attempt to access beyond end of device
[  376.064000] sdb: rw=0, want=7821157, limit=2009088
[  376.064000] FAT: Directory bread(block 7821156) failed
[  376.064000] attempt to access beyond end of device
[  376.064000] sdb: rw=0, want=7821158, limit=2009088
[  376.064000] FAT: Directory bread(block 7821157) failed
[  376.064000] attempt to access beyond end of device
[  376.064000] sdb: rw=0, want=7821159, limit=2009088
[  376.064000] FAT: Directory bread(block 7821158) failed
[  376.064000] attempt to access beyond end of device
[  376.064000] sdb: rw=0, want=7821160, limit=2009088
[  376.064000] FAT: Directory bread(block 7821159) failed

---

### Post by trippinnik on 2007-09-16
Are you certain your card reader supports SDHC?  It's a newer standard so it's not quite common yet.  The problem you are describing would be caused by having a reader than only understands the original SD standard.

---

### Post by psusi on 2007-09-16
It appears that the hardware is reporting it is only a 1 gb card, and your attempts to access beyond that are failing.

---

### Post by krandun on 2007-09-16
Woah, nice call. I didn't even think to check for hardware problems. :oops:

I pulled the external card reader I've been using on my Windows machine and plugged it into this Linux box. Like magic, 4GB all the time, no complaining! I'm copying files over now.

Thank you psusi for not giving up on me.
Thank you trippinnik.

---

