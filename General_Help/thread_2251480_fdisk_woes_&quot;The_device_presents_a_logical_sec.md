---
title: "fdisk woes: &quot;The device presents a logical sector size that is smaller than...&quot;"
date: 2014-11-04
forum: General Help
---

### Post by ooboontwo on 2014-11-04
**SOLVED; SEE EDIT BELOW.**

Hello everyone,

I am running Ubuntu Server 14.04.1 LTS.

The OS is installed on /dev/sda (a SanDisk SSD).

I am trying to format an additional drive (/dev/sdb) as ext4 for storage space.

When entering **fdisk /dev/sdb** in the terminal I receive the following message:

> "The device presents a logical sector size that is smaller than the physical sector size. Aligning to a physical sector (or optimal I/O) size boundary is recommended, or performance may be impacted."

Now, Google tells me that this has to do with the type of drive I am running. Something about being aligned to 4k instead of 512. The answer I found elsewhere said to create a new partition with starting/ending sectors divisible by 8.

Therefore, I ran **fdisk /dev/sdb** and then **'n'** to create a new partition. I selected **'extended'** instead of primary (because I don't need to boot from this drive but if there is some other good reason to select primary over extended please let me know).

Next I went with the default starting sector, which was 2048 and is divisible by 8. Finally it asked for the last sector.

The default last sector was 3907029167, which is not divisible by 8. I changed this to 3907029160 (the nearest sector divisible by 8). I then entered **'w'** to write the changes.

However, when I enter fdisk /dev/sdb again, I receive this same error:

> "The device presents a logical sector size that is smaller than the  physical sector size. Aligning to a physical sector (or optimal I/O)  size boundary is recommended, or performance may be impacted."

So, am I understanding this right? Should I ignore this message? Otherwise, how can I correct it?

I also apologize if this is not the correct forum for such a question. I debated posting it in the Server forum but since it really has to do with my HDD and not the OS directly, I thought I would post it here. I also thought about putting it under Hardware, but yet again I am dealing with fdisk which is software and my problem isn't the disk itself so much as the partitioning of the disk.

Mods, please feel free to move somewhere more appropriate if necessary.

Thank you in advance for your help.

[B]SOLUTION:

[/B]First, I discovered that this message is just a warning, a friendly heads-up that my drive is a 4k drive instead of the traditional 512b.Next, I found a command that (supposedly) ensures proper 4k alignment when creating new partitions with fdisk.

```
fdisk -H 224 -S 56 /dev/sdb
```

However, I was still having trouble formatting it. Whenever I went to format the partition using:

```
mkfs.ext4 /dev/sdb1
```

I would receive an inode error message. I solved this error message by selecting 'primary' partition in fdisk, rather than 'extended.' Honestly, I have no idea why this made a difference but it did. Perhaps all drives must have one primary partition? I don't know, but it works and my problem is solved. Hopefully other Googlers will find the fdisk command above to be helpful. ;)

---

### Post by oldfred on 2014-11-05
Some BIOS require a boot flag on a primary partition. But grub does not use one, so those BIOS must assume Windows. So best to have a primary partition and include boot flag even if just a data drive.

But most Linux only systems would be better with gpt partitioning. You use gdisk which is the fdisk for gpt drives and in the repository.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Windows only boots from gpt with UEFI, but Ubuntu will boot from a gpt partitioned drive with either BIOS or UEFI. And if a data drive only XP will not read a gpt partitioned drive. I have used gpt on one drive since 10.10 and now on all new drives whether UEFI or BIOS boot.

      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

