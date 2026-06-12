---
title: "Tried fixing HD MBR, messed with the partition accidentally"
date: 2015-05-27
forum: General Help
---

### Post by luiz6 on 2015-05-27
So I deleted my Ubuntu partition and yadda yadda can't boot the PC, never mind about that. I was following instructions from other threads and such and managed to get a flash drive to boot Ubuntu with, and in it I used the following command to fix my booting problem: [I]

sudo dd if[/I]=/usr/lib/syslinux/*mbr*.bin of=/dev/sda

but in typing I actually put *sda1* instead, altering the partition, so now Gparted can't find a file system and I can't access its files.

I've tried fixing but I'm not sure what to do, since all the similar cases I've found are of people who used the *dd* command to overwrite the whole partition or something, so I don't know if it's the same case. Is this fixable? And how so?

The disk in question has only the one partition which contains my personal files and operating system, and I don't have access to my Windows CD. The whole booting problem is a separate issue that needn't be addressed here, there's plenty of info on that out there.

Thank you for reading, hope you can help me :(

---

### Post by VMC on 2015-05-28
You just wrote mrb.bin out to partition 1 of sda. You might have just overwritten Windows boot partition only, if lucky. 'dd' is a very ***dangerous*** command, as you are now aware.

Boot up ubuntu and open gparted and it will show you if anything is left.

Or if your familiar with the command line Terminal, type:
 [FONT=monospace][COLOR=#000000]```
sudo parted -l /dev/sda
```[/COLOR]
[/FONT]

---

### Post by Bucky Ball on 2015-05-28
Welcome. _Don't_ boot from that disk. You have just overwritten whatever was on sda1 and from what you're saying that is Windows and your personal files. If you want to retrieve what was on it, boot from Live media, NOT the disk. Check these links:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Testdisk may be able to retrieve your partitions, Photorec your files. Go Testdisk first.

---

### Post by oldfred on 2015-05-28
If the NTFS partition, it keeps a backup of its partition boot sector.
Testdisk can restore from the backup if the backup is valid or build a XP type NTFS new boot sector.

       As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

### Post by luiz6 on 2015-05-28
Edit: I sent this before seeing the above post, gonna try it now

Edit 2: seems to have worked! Gparted recognizes the file system now. Half the hd is full, but I can't remember how much of it was actually full before. I'm working on Photorec now, thank you.

---

### Post by luiz6 on 2015-05-28
It's solved! 

I let PhotoRec run for a while (lots of data on my drive), but then Ubuntu froze.

I restarted and ir turns out all the files are there, no need for PhotoRec, OldFred's instructions were enough to fix my mistake.

Thank everybody so much!

---

### Post by Bucky Ball on 2015-05-29
Great news and well done. ;)

Please mark thread as solved (see second link in my signature) to help others. This won't close the thread for further discussion. Good luck. ;)

---

