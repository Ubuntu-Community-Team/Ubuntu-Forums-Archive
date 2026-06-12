---
title: "Move data in MBR Partitioned System, to a GPT Partitioned System?"
date: 2014-12-21
forum: General Help
---

### Post by mikodo on 2014-12-21
Hi,

Can I use a new, GPT partitioned, internal drive install of Xubunut 14.04, to read and copy data to a GUID "data" partition, from an external usb drive, that has the "data"partition in a  (UUID) logical partition?

Thank you.

Edit: Title changed to more aptly describe question.

---

### Post by sudodus on 2014-12-21
***GUID*** is a kind of partition table. ***UUID*** is a way to identify a partition, that belongs to the file system. Linux ***ext*** file systems have a long UUID string, while ***FAT*** and ***NTFS*** file systems have a shorter UUID string (in the same partition container).

It should work without problems to copy data to a GPT partitioned drive from a standard drive (with an MSDOS partition table). The critical thing is the file system. If both file systems are linux file systems, there will be no problems with the file permissions and ownership.

If one of the file systems is FAT or NTFS, the files will be copied, but you may not copy the file permissions correctly, because linux sets the permissions for the whole FAT or NTFS file system (instead of managing it for each individual file). This is usually no problem with personal data files, but system files (program files, program settings, desktop settings etc) are sensitive.

---

### Post by mikodo on 2014-12-21
> **sudodus said:**
> 
It should work without problems to copy data to a GPT partitioned drive from a standard drive (with an MSDOS partition table). The critical thing is the file system. If both file systems are linux file systems, there will be no problems with the file permissions and ownership.
Thank you.

I apologize. I know I was not able to properly explain/name what I was asking.

Basically, I want to change from using a MBR Partitioning System, to the GPT (GUID Partitioning Table).

I plan to put a new internal drive in, format it with GPT, and move my data from my external drive's "data partition", (which for now, is still using the MBR  partitioning system), to a GPT "data partition", in the new drive.

Since they both will be formatted with an ext4 file system, I should be all right. I guess, it doesn't matter how it is partitioned.

---

### Post by sudodus on 2014-12-21
Yes, it should work.

Do you intend to copy only some personal files, or the whole system? If the whole system, you must install the bootloader, and if you change the UUIDs of the system partition(s), root (and maybe home) and swap, it must be edited into /etc/fstab.

*Edit*: and /boot/grub/grub.cfg

---

### Post by mikodo on 2014-12-21
> **sudodus said:**
> Yes, it should work.

Do you intend to copy only some personal files, or the whole system? If the whole system, you must install the bootloader, and if you change the UUIDs of the system partition(s), root (and maybe home) and swap, it must be edited into /etc/fstab.

*Edit*: and /boot/grub/grub.cfg

Thank you, again!

To sudodus: It will only be data that I am going to transfer from  backup, to place in a new GPT partitioned ext4 FS, for sym-linking to my  /mnt, in my to be newly installed Xubuntu 14.04. Thank you, for your  patience and advice.

For any other casual user, who might wonder about this and may be searching and finds this thread, below are some links, I have been reading, which also include how to edit fstab for GUID's, and to install the bootloader, if one is doing this for a whole presently installed distro:

                        [http://www.linux.com/learn/tutorials/730440-using-the-new-guid-partition-table-in-linux-good-bye-ancient-mbr-](http://www.linux.com/learn/tutorials/730440-using-the-new-guid-partition-table-in-linux-good-bye-ancient-mbr-)
 

                           [http://www.rodsbooks.com/gdisk/gdisk.html](http://www.rodsbooks.com/gdisk/gdisk.html)


                    [http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)


                        [URL="https://en.wikipedia.org/wiki/GUID_Partition_Table"]https://en.wikipedia.org/wiki/GUID_Partition_Table


[/URL]

---

### Post by oldfred on 2014-12-21
Do not use any image copy type tools to copy to gpt partitions, they have internal structures that must not be copied.

But I just built new computer and my data partition was on an old MBR drive and new drive is gpt.
I just used rsync. numbers are just the order in my history file.

  32  rsync -aruvlP /media/fred/Data/ /mnt/data
   33  rsync -aruvlP /media/fred/Shared/ /mnt/data

My Shared was a NTFS data partition as old system had XP. New system will not have any Windows so all data is now in Linux formatted data partition.

I then reset my permissions & ownership
 37 sudo chmod -R a+rwX,o-w /mnt/data
   38  sudo chown -R $USER:$USER /mnt/data

---

### Post by mikodo on 2014-12-21
> **oldfred said:**
> Do not use any image copy type tools to copy to gpt partitions, they have internal structures that must not be copied.

Thank you Fred, for the explanations and the examples. I will use the rsync scenario most likely too. I already have your examples to use for the ownership, permissions and rsync commands saved, from earlier communications here. But, it is nice to see again, how you do it.

Wow! Part of my backup scenarios, were to start using using Clonezilla with it's partclone features for mission critical stuff, to a separate storage medium on top of regular rsync backup of the entire data partition's data, to an external drive. I didn't know I couldn't image the partitions on GPT! That's not good. This has me wondering if I really need to go from a MBR partition system to a GPT partition system. hmm ... Well, it doesn't matter I guess, I can rsync the mission critical stuff, to it's separate medium, just as well, (for portability to a relative's home).

:p

---

### Post by oldfred on 2014-12-21
You can use a full drive image or full drive dd, just not partitions.

 Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
Do not use dd with gpt partitions. Whole drive ok if old drive not used anymore, or no duplicates.
But do not use dd for copies from MBR to gpt partitioned drives, can use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
Restore full drive dd backup - resync gpt partition tables and fsck pursuvant
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

I have always preferred with Ubuntu to only backup my data & settings. As it is easy with Linux to download or have a full install copy of the operating system. And then I just need to restore my settings & run updates if I have to restore to a new drive after a drive failure. Not much different than what I did when moving system from old BIOS hardware to new UEFI hardware which had to be a new install anyway because of the major sytem reconfiguration.

---

### Post by mikodo on 2014-12-21
> **oldfred said:**
> I have always preferred with Ubuntu to only backup my data & settings. As it is easy with Linux to download or have a full install copy of the operating system. And then I just need to restore my settings & run updates if I have to restore to a new drive after a drive failure.
+1

This question in askubuntu.com has good answers on how to do this. See the link.

[http://askubuntu.com/questions/9135/how-to-backup-settings-and-list-of-installed-packages](http://askubuntu.com/questions/9135/how-to-backup-settings-and-list-of-installed-packages)

Well Fred, we have gone off topic a little. But, it is *important stuff. ;)

Kind Regards.

---

