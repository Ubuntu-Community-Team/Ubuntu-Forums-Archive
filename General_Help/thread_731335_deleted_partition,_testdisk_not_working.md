---
title: "deleted partition, testdisk not working"
date: 2008-03-21
forum: General Help
---

### Post by wouterke on 2008-03-21
Hi 

I acedentilly deleted the ext partition on my port HD (1 single partition, the entire drive)
when i try testdisk it finds the partition no problem, but it claims the partition can't be recoverd 

> Disk /dev/hdb - 160 GB / 149 GiB - CHS 19457 255 63

The harddisk (160 GB / 149 GiB) seems too small! (< 160 GB / 149 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 19457  80 62  312581744



i alreaddy tried taking the drive out of the usb enclosure and hooked it up to the pc diectly but with the same result

does annyone know  of annything that might help?


thanks 

Wouter

---

### Post by danwood76 on 2008-03-22
If the partition was the entire disk you could try rebuilding the partition table manually.

First check that the partition table is empty:
```

sudo fdisk -l

```

you shouldnt see any /dev/sdb1 (or sdbx) entries.
If you do then you already have a partition on the drive.

If its clear then rebuild the partition table as folows:
first start fdisk:
```

sudo fdisk /dev/hdb

```
press 'n' for new partition.
```

Command action
   e   extended
   p   primary partition (1-4)

```
Then 'p' for primary.
```
Partition number (1-4):
```
Then '1' for partition 1.
```

First cylinder (1-xxxx, default 1):

```
Just press enter for the default (this should be 1)
```

Last cylinder or +size or +sizeM or +sizeK (1-xxxx, default xxxx):

```
Hit enter again for the maximum size of the disk.

If you then hit 'p' you should get a print out of the partition table stating that the partition you just created has a linux ID (83).

If this is correct then hit 'w' to write the contents of this partition table to the disk.
You will then need to reboot for the new drive structure to be loaded.
Once rebooted you should be able to mount the drive.

Any problems please post the fill output of the terminal as it will help a lot.

regards,
Danny

---

