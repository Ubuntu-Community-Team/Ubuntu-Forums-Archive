---
title: "Cloning a disk to a smaller disk"
date: 2019-09-24
forum: General Help
---

### Post by orthoducks on 2019-09-24
I need a simple, reliable way to clone a disk to a smaller disk. Ideally it should work for both GPT and MBR drives, and should use only software on a Ubuntu 18.04 live disk.

I'm thinking about this: shrink partitions with GParted, copy the MBR and each partition with dd, and rebuild the partition table with GParted. I'm pretty sure this will work on an MBR disk, but I'm not sure about GPT.

Cloning the disk with Clonezilla would be simple -- in theory -- but I swore never to use it after getting in a situation where it wouldn't copy one partition because of a corrupted filesytem, and none of the repair tools I tried could find corruption to repair. This problem has me thinking that perhaps I can make peace with Clonezilla, or at least use it for this occasional operation and hope it doesn't go haywire again...

---

### Post by uRock on 2019-09-24
I've booted from LiveCD and used Gparted to copy partitions from one to drive to another. Whenever the target drive is shorter, I just shrink the partition on the old drive first, then copy it over. If the drive you're copying is Windows, then it is best to shrink the partition within Windows first, then boot the live CD and use DD or gparted to copy it over.

---

### Post by orthoducks on 2019-09-24
How do you handle the master boot record?

---

### Post by uRock on 2019-09-24
They partition table had already been created, but you are able to do that through Gparted if needed. Since I was moving a dual boot from one system to another, I just removed the old HDD, so the new SSD was the only thing connected, then booted the liveUSB and ran **sudo update-grub** and it was good to go from there.

---

### Post by TheFu on 2019-09-24
Just throwing out a few ideas.

Best not to use dd. ddrescue will handle any faults, while still doing a byte-for-byte copy.  dd can work for MBR partitions, but not for GPT. In GPT, there are 2 copies, placed on opposite ends of the disk.  

The only tool I know that will do a bit-for-bit copy, yet allow restore to a smaller partition doesn't work at the disk level. It works at the partition level.  **fsarchiver**.  fsarchiver will capture the file system during the backup and lay down the same file system during a restore.  It is more efficient if the tool understands the file system, but it can handle anything at a binary level.  *savefs* is the command option. There's a *restfs* to go the other way. The manpage has nice examples.

As for creating disk partition tables, you can use **sudo parted -ml** to capture a current table and use that machine readable output as input to create a partition table on any other disk with the specified sizes and partition types. An example:
```
BYT;
/dev/sda:500GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:1305MB:768MB:ext2::;
3:1305MB:500GB:499GB:::;

```
sda3 holds a LUKS encrypted container which holds LVM inside with PVs, VGs and LVs.
vgcfgbackup and vgcfgrestore would probably be helpful. I've never used either.  My backups are performed above the file system layer.

Here's the sfdisk for the same:```

$ sudo sfdisk -l   /dev/sda
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 20A94340-1AE2-405A-9C90-xxxxxxxxxxxxxxx

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2549759   1499136   732M Linux filesystem
/dev/sda3  2549760 976771071 974221312 464.6G Linux filesystem
```
To me, all the interesting stuff is in sda3.

Perhaps there are commercial options. I wouldn't know about those. If they are Windows-centric, they likely wouldn't know anything about LVM or LUKS encryption.

---

### Post by VMC on 2019-09-24
Understanding your file systems would help us more
```
lsblk -f
```.

---

### Post by orthoducks on 2019-09-25
A few responses.

I appreciate the suggestions of dd_rescure and fsarchive, but as I said in the OP, part of the idea here is to use only tools in the distro. If I need my own customized live Ubuntu, that's a serious disadvantage; I may be in situations where I have to create it over and over.

VMC, I'm not sure what you want to know about the disk, and the system isn't at hand now, but from memory, the partitions are:

1. GRUB partition created by the Linux installer.
2. Windows system partition: NTFS
3. Extended partition (I happen to be working on an MBR drive)
4. Shared data partition: NTFS
5. Linux system partition: ext4

2 and 5 have large amounts of empty space which I'm trying to reduce. 3 is just a container. 4 is empty.

---

