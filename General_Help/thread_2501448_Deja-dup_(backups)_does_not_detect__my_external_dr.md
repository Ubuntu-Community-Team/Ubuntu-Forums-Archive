---
title: "Deja-dup (backups) does not detect  my external drive"
date: 2024-10-08
forum: General Help
---

### Post by Acharn on 2024-10-08
I recently accidentally installed kubuntu on my backup drive. I deleted it by making a new partition table and a new partition. When I tried to backup my drive with Backups (deja-dup), it said, "Waiting for '1.0 TB drive' to become connected." I've tried formatting, making new partitions, unplugging the drive in every combination I can think of. I even uninstalled deja-dup and reinstalled it. I've unmounted and remounted, and rebooted the machine. Nothing has worked so far. Any suggestions? I'm running Ubuntu 24.04, and I'm willing to use a different backup program.

---

### Post by yancek on 2024-10-08
Boot Ubuntu and post the output of the command:  sudo parted -l   Only need the information of the drive in question.  Does it show?  How are you trying to access the drive?  Does it show up under /media/username?  Are you mounting from a terminal?  What command did you use?  Are you able to access the drive partition at all or is it just when you use the specific software?

---

### Post by deadflowr on 2024-10-08
Did you reset the backup location in deja-dup to match the newly created partition?

---

### Post by Rubi1200 on 2024-10-08
> **deadflowr said:**
> Did you reset the backup location in deja-dup to match the newly created partition?
Seems to me that might be an obvious first place to check.

You should also check UUIDs and mount points with **lsblk -f** and check your **fstab **file

---

### Post by Acharn on 2024-10-08
The part of 'sudo parted -l' that refers to the external hard drive is:
```

Model: WD Elements 25A2 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1000GB  1000GB  fat32              msftdata

```
The drive is automatically mounted, I presume by fstab, on bootup.
I have tried changing the name of the folder, from 'henry' to 'backup,' but it still says "waiting for '1.0 TB drive' to become connected."
The drive gives every appearance of being mounted, as it has been for the past year. I don't do anything to mount it. It just shows up in the launcher, or whatever that thing at the left side is. 
I'm able to create folders and to write files to the drive with vi. When I created a new partition it deleted the previous backup folder; I created a new one with the same name with "sudo mkdir /media/roger/AA86-F663/henry."

---

