---
title: "Creating a new partition on my o/s HD - how to"
date: 2016-09-23
forum: General Help
---

### Post by ra7411 on 2016-09-23
[FONT=&amp] I have a 2 terabyte hard disk with Ubuntu OS installed  separate from  my home partition.   Only 3% of the  2 terabytes is being used and I  want to create a new partition for back up. The /home partition is ~1.8 tb, most of which is free.

[/FONT][FONT=&amp] I'm thinking that  I need to re-start with the install disc and use gparted to create the new partition.
[/FONT][FONT=&amp]Is that correct, or is there some easier way of doing it?[/FONT]
[FONT=&amp]Thanks[/FONT]

---

### Post by ajgreeny on 2016-09-23
> **ra7411 said:**
> [FONT=&amp] I have a 2 terabyte hard disk with Ubuntu OS installed  separate from  my home partition.   Only 3% of the  2 terabytes is being used and I  want to create a new partition for back up. The /home partition is ~1.8 tb, most of which is free.

[/FONT][FONT=&amp] I'm thinking that  I need to re-start with the install disc and use gparted to create the new partition.
[/FONT][FONT=&amp]Is that correct, or is there some easier way of doing it?[/FONT]
[FONT=&amp]Thanks[/FONT]
Quite correct, but depending on the boot mode (BIOS or UEFI) and what partitions are already on the disk  you may run into problems of the limit of 4 primary partitions possible.  If using GPT partition table there is no problem at all but you will have to have a small partition either for grub or for the EFI boot files.

Show us the output of ```
sudo parted -l
``` in terminal and we can help you in more detail.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by ra7411 on 2016-09-23
[B]It's a bios setup.

```


```[/B]```
Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  50.0GB  50.0GB  primary   ext4            boot
 2      50.0GB  2000GB  1950GB  extended
 5      50.0GB  59.0GB  8999MB  logical   linux-swap(v1)
 6      59.0GB  2000GB  1941GB  logical   ext4




Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext4




Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4

```

---

### Post by yancek on 2016-09-23
Your home partition is on a logical partition within the Extended partition so you should have no problem shrinking it from the install disk with GParted.  Make sure you unmount it first.

---

### Post by ajgreeny on 2016-09-23
> **yancek said:**
> Your home partition is on a logical partition within the Extended partition so you should have no problem shrinking it from the install disk with GParted.  Make sure you unmount it first.
This is correct, but you will also need to right click on the swap partition in gparted and choose **Swapoff** as it will be used by default when found by the live system, and if not turned off will stop you doing anything to the partitions in the extended sda2, including your large home partition.

---

