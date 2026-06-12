---
title: "what is this 17 mb volume? can i disable it or hide it?"
date: 2024-06-19
forum: General Help
---

### Post by ronjjjg8885 on 2024-06-19
tnx[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293891&stc=1[/IMG]

---

### Post by TheFu on 2024-06-20
Don't know from the information provided.  
The only answer is "it depends."

---

### Post by ActionParsnip on 2024-06-20
Is this  a dual boot?

---

### Post by yancek on 2024-06-20
Looks like the size for a Microsoft reserved partition for windows which you can find by simply running sudo fdisk -l and look for /dev/sda2 and on the right on that line, check the Type column.

---

### Post by TheFu on 2024-06-20
If we are talking commands, then the 3 I'd need are:
```
sudo parted -l
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
sudo lvs
```

Please post the command AND the output wrapped in forum code tags so the columns line up correctly. Without code tags, it is too easy to make mistakes interpreting the data.

---

### Post by ronjjjg8885 on 2024-06-20
it's a new computer with only ubuntu. there was never windows on it.
but i do have a data hard drive that i transferred from the old computer and which does not contains any windows  files but only used for back up.
```
not-pc@not-pc:~$ sudo parted -l
[sudo] password for not-pc: 
Sorry, try again.
[sudo] password for not-pc: 
Model: ATA ST2000DM008-2FR1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 2      1049kB  17.8MB  16.8MB  ext4
 1      17.8MB  2000GB  2000GB  ntfs         Basic data partition  msftdata


Model: WD Blue SN580 1TB (nvme)
Disk /dev/nvme0n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1128MB  1127MB  fat32              boot, esp
 2      1128MB  1000GB  999GB   ext4


not-pc@not-pc:~$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME       TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
sda        disk          1.8T                      
&#9500;&#9472;sda1     part ntfs     1.8T                      
&#9492;&#9472;sda2     part ext4      16M       0    97%       /media/not-pc/d2469e7d-0ae1-4
nvme0n1    disk        931.5G                      
&#9500;&#9472;nvme0n1p1
&#9474;          part vfat       1G      1G     1%       /boot/efi
&#9492;&#9472;nvme0n1p2
           part ext4   930.5G  849.2G     2%       /
not-pc@not-pc:~$ sudo lvs
sudo: lvs: command not found
not-pc@not-pc:~$ 


```

do you need the other command too?
tnx

---

### Post by TheFu on 2024-06-20
**TL;DR:**
So, back to your original question ... can you hide or delete the 16.8MB partition on the SATA drive?  Yes, but I'd say you should delete both partitions and create 2 new ext4 partitions. What's important is NOT having NTFS and using native Linux file systems on a Linux system.

**Longer answers ... for questions you didn't ask ... **

lvs is only needed when LVM is being used.  You aren't using it, so no, not needed.

If we look at the output from parted ...
Both are using GPT. Excellent.

The NVMe has:
```
Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1128MB  1127MB  fat32              boot, esp
 2      1128MB  1000GB  999GB   ext4
```

That says you are using UEFI to boot (fat32) and that you've accepted the crappy default for / sizing being much, much, too large.  That's a choice, but not one that more experienced Linux people would choose.  

The 2TB SATA drive, 
```
Number  Start   End     Size    File system  Name                  Flags
 2      1049kB  17.8MB  16.8MB  ext4
 1      17.8MB  2000GB  2000GB  ntfs         Basic data partition  msftdata
```
So you have 2 partitions there - NTFS (yuck!) and EXT4.  Looks to me like the HDD came with NTFS by default and you didn't fix that.  For almost all Linux backups, we need a native linux file system on the target, so NTFS doesn't fit that requirement.  If it were me, I'd wipe the drive completely, then split it in half - how you do that with partitions or with LVM or ZFS volume management is up to you.  I'd use LVM.  I don't like to have my backup storage larger than my main drive.  There are some reasons for this, but just know that it prevents issues later.  

There's ZERO reason to have any NTFS inside a 100% Linux system.  ZERO.

As you can see, that lsblk command (worth making an alias for IMHO), provided more, but similar information.  Sometimes parted will see things that lsblk doesn't see.  That's why both are needed.

I've posted my ideal disk partitioning/layouts in these forums a number of times over the last decade. There are reasons for everything I do.  For the most simplistic setup, I'd insist on at least 4 partitions.
1. UEFI - fat32 - 50MB - recommendations are for 500MB, but on my systems, I've never used more than 10MB.  I think larger sizes are needed when there are many other OSes, so if you plan to install others, it is 100x easier to make it bigger at install time than later.
2. Swap - 4.1GB is the only size for a swap partition for any Desktop system.  This is the minimum for low-RAM systems and for systems with lots and lots of RAM, 4GB will allow you (or any user) to "feel" the slowdown when swap is fully used.  On a busy system, 
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        21Gi       1.8Gi       200Mi       7.4Gi       8.5Gi
Swap:         4.1Gi       2.6Gi       1.5Gi
```
My swap is 4.1G and 2.6G is being used even with over 8G of real RAM still available.  I ran that system with 16GB of RAM and started noticing slowdowns as it got closer to being fully used.  DDR4 RAM is cheap, so doubling it wasn't too expensive and has provided convenience in not having to worry about hitting the new real RAM limits.
3. / - 35G but never over 50G - some native Linux file system, probably ext4 unless you have a specific reason to use something else.  Keeping the OS and programs separate from "data" is important. It makes some common things easier later, like reinstalls and upgrades. Because we've setup a separate swap partition, we don't have any need for a swapfile, so if the installer makes one, turn it off (/etc/fstab) and delete the file. That's 4G not wasted in /.  Since the very beginning, swap partitions have been part of Linux. Swapfiles are relatively new and still file sometimes.
4. /home - whatever size you need, but if you do the layout in a smart way, you'll be able to extend it as needed.  For example, I consider 20G for /home to be way, way, too much.  If you keep large data on a specific data partition or on the network in a NAS/NFS device, you'll be able to manage trash in your HOME easier.  Keeping it small along the way prevents discovering 9 months later that the HDD is completely full and mostly with crap.

If you are interested in a more secure system, that can be improved by having a few more partitions and using mount options to prevent some capabilities.  I like to put virtual machines in a specific "partition" and LXC containers in a different "partition".  I put quotes around that word, since I use LVM and really it is a "Logical Volume", not a partition.  LVs provide capabilities and flexibility that partitions do not. It is one of those choices that is best made at install time, alas, 24.04 desktop installers seem to have broken all LVM support at install.  Fortunately (for me) the 24.04 Ubuntu Server install still does LVM no problem.  I will not be installing a 24.04 Ubuntu desktop until LVM is supported. It is central for my storage management and especially for getting clean backups.

Only you can decide if dealing with LVM or a volume manager is worth it. Almost always, I use the "do something else" option in the storage setups, unless it is a toy system and will never be used for "production".  *Toy* means it will be wiped/deleted within a few weeks and storage isn't central for the purpose of the system.

BTW, if you give those partitions on the SATA drive each a LABEL, then you can use that LABEL to mount each. This is much easier than dealing with the human-unfriendly UUIDs.  gparted can do the partitioning and set the label.

---

### Post by grahammechanical on 2024-06-20
> 1      17.8MB  2000GB  2000GB  ntfs         Basic data partition  msftdata

It is a Windows partition. Does the File Manager open it? That will reveal if it has any files in it. Also, the Disks utility will show how much of the 17.8 MB is being used. It will give you confidence about deleting the partition.

Regards

---

### Post by ronjjjg8885 on 2024-06-21
i'm not a savvy.
it was hard to comprehend.
hopefully it can be explained more simply.
thank you anyway..

---

### Post by ronjjjg8885 on 2024-06-24
i wish things were more simple

---

### Post by TheFu on 2024-06-24
> **ronjjjg8885 said:**
> i wish things were more simple

Simplicity is likely what got you what you have today.

---

### Post by yancek on 2024-06-24
Since you indicate the only OS you have is Ubuntu 24.04, there is not need for an ntfs filesystem on any partition.  That is only used for sharing data with a windows OS.  So as suggested above, create a partition or partitions on that drive using Ubuntu with ext4 or another Linux filesystem.  I"d be interested in knowing how a 17MB ext4 filesystem partition came to be on that drive.  The only partition type that small that would be useful would be a bios_boot partition which only needs to be 1-2MB and would NOT be formatted with any filesystem.

Have you tried the suggestion to create a mount point for /dev/sda2 and mount it to see what if anything is on it.  Thousands of sites explaining how to create a mount point and mount a partition.

---

