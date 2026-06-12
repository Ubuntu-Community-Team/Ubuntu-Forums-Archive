---
title: "Issue with 16.04 booting with encrypted drive"
date: 2016-08-18
forum: General Help
---

### Post by jordanja72 on 2016-08-18
I am running 16.04.1 on a Dell Latitude D620 laptop with encryption at the drive level. It has been running well for some time; however, yesterday after installing fiddler, it hung on me and I had to hard boot it. When it came back up, it gave me the encryption password page, but then went to a command like screen that mentioned 'busybox' and 'initramfs' and would not boot. I booted via Live cd and am able to get in and see my drives; however, I can't access the data under the /home/*username* directory - so i can't even copy off to another system. I tried a number of things I found online, including boot repair and selecting another superblock, but no luck. I will lose some important data if I have to reimage, so I really would like to at least be able to access that so I can save off. I am not sure what data is needed, so please let me know if additional info is needed.

**Fdisk results:**[INDENT]Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes[/INDENT]
[INDENT]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/INDENT]
[INDENT]Disklabel type: dos
Disk identifier: 0x00078b33

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 312580095 312078338 148.8G  5 Extended
/dev/sda5       501760 312580095 312078336 148.8G 83 Linux


Disk /dev/mapper/luks-121d15d1-8fd5-4f71-b447-227ad4b1b8e2: 148.8 GiB, 159782010880 bytes, 312074240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-root: 146.8 GiB, 157638721536 bytes, 307888128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 2 GiB, 2139095040 bytes, 4177920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
[/INDENT]

**GParted results:**[INDENT]_Partition  |  File System  |  Mount Point                                                                |  Size_
/dev/sda1  ext2                /media/ubuntu/1611f4a0-af1b-441a-ab71-6e3da4b3909a     243.00 MiB
/dev/sda2  extended                                                                                              141.81 GiB
/dev/sda5  crypt-luks                                                                                             141.81 GiB
[/INDENT]

---

