---
title: "dd to sd cannot be read get ext4 right"
date: 2017-04-17
forum: General Help
---

### Post by ELMIT on 2017-04-17
I am trying to use a ASUS tinker board. ASUS suggest a Debian image.

I use this commands to get the image to the SD card:
```

DEVICE=/dev/sdd
echo $DEVICE

/dev/sdd   # means ok

test -b $DEVICE || echo "ERROR with ${DEVICE:-device}"
# no output, ... means ok

IMAGE_NAME=$(ls | grep .jessie-alip)
echo $IMAGE_NAME

20170223-tinker-board-linaro-jessie-alip-v14.img
# means ok

DEV=${DEVICE/disk/rdisk} ; test -b $DEV && sudo dd if=$IMAGE_NAME of=$DEV seek=0 bs=16M conv=notrunc || echo "ERROR writing $DEV"
98+1 records in
98+1 records out
1652129792 bytes (1.7 GB, 1.5 GiB) copied, 378.14 s, 4.4 MB/s


```

Now it comes the fun part:
```

sudo parted -l

...
Model: Generic- SD/MMC (scsi)
Disk /dev/sdd: 31.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  71.3MB  67.1MB  primary  fat32        lba
 2      71.3MB  2219MB  2147MB  primary  ext4


```

using: sudo gparted and go to that drive I see a ! at the ext4 partition
The Info menu shows then:

540.41 MiB of unallocated space within the partition.
To grow the file system to fill the partition, select the partion and choose menu item:
Partition -> Check

It does not matter if I do that or not. After inserting the sd card to the ASUS tinker board, it reboots many times, trying to mount the Ext4 as ext3, then ext2 and give me then a graphic screen (black) with a box telling me:

One or more XML syntax errors were found while parsing the Openbox configuraion files. Se stdout for more information. The las error seen was in file "/home/linaro/ifconfig/openbox/xde-rc.xml line1 with message: Document is empty.



Any idea?

---

### Post by TheFu on 2017-04-17
did you validate the image file you shoved onto the storage? Could it be corrupt?

---

