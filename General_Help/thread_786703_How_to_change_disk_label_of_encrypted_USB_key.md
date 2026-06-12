---
title: "How to change disk label of encrypted USB key?"
date: 2008-05-08
forum: General Help
---

### Post by iggee85 on 2008-05-08
I used luksformat to encrypt a 2GB usb key and it changed the name of the drive to "2.1 GB Media". I couldn't find any options (GUI or command-line) to manually set the disk label. It's not a big deal but I was wondering if there's a way to do this.

---

### Post by nick_h on 2008-05-11
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by iggee85 on 2008-05-12
I already tried that method but it doesn't work probably because it is an ecrypted drive, here's the error message I get:

> e2label: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

---

### Post by nick_h on 2008-05-12
I don't use encrypted drives myself but from what I have read you should be using a device name /dev/mapper/name rather than the raw device /dev/sdb1.

---

### Post by bodhi.zazen on 2008-05-12
You need to first decypt the device, then you can change the label.

---

### Post by F W Adams on 2008-09-06
I'm also getting the problem of not being able to change the label of an encrypted drive partition.

I have a USB disk with two partitions, only one encrypted. The instructions from post #2 work fine on the unencrypted partition but not on the encrypted. If you try putting on a label before encrypting the partition the encrypting process overwrites the label.

I'm using FAT32. Here's what I get with the irrelevant bits taken out.

felix@felix1:~$ sudo fdisk -l
Disk /dev/sdg: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        2040    16386268+   b  W95 FAT32
/dev/sdg2            2041        9729    61761892+   b  W95 FAT32
felix@felix1:~$ sudo mlabel -i /dev/sdg2 -s ::
init :: non DOS media
Cannot initialize '::'
mlabel: Cannot initialize drive
felix@felix1:~$ 

The name defaults to a meaningless "63.2 GB Media".

---

### Post by joonR on 2010-06-28
> **nick_h said:**
> You should be using a device name /dev/mapper/name rather than the raw device /dev/sdb1.

This is true. I have struggled with this a little bit as well. 

While the drive is mounted, get the device name with mount:

$ mount
/dev/dm-0 on /media/500GB_ext4 type ext4 (rw,nosuid,nodev,uhelper=devkit)

$ e2label /dev/dm-0 NewName

Now unmount the drive, and mount it again, and you should see the changed label.

---

