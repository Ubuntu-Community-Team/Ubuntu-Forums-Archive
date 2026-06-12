---
title: "Can't see hard drives, nor External Hard Drives"
date: 2017-07-14
forum: General Help
---

### Post by xanderforrest on 2017-07-14
I installed Ubuntu Unity from a Linux Format magazine on my 2tb hard drive.

Added 2 more 1tb hard drives.

Couldn't se ethem in file manager but found in Disks and formatted both.

THe only time I ever see them is in disks. Can't access them at all. I desperately NEED to store data on these. I like organization. I've installed every tool, every patch, looked at every forum thing. I just want something like "My Computer" on Windows. 

I can also see my external hard drive on Disks. But again, it doesn't show up like flash drives do.


Please please please help me. I'm so desperate rn and don't want to go back to Windows..

---

### Post by deadflowr on 2017-07-14
How'd you format them, file system type-wise?

---

### Post by xanderforrest on 2017-07-14
I did the full one, not encrypted but not just 0's. It's not just because thye were formatted because the externeral also doesnt work ):

---

### Post by deadflowr on 2017-07-14
Open a terminal and run
```
sudo parted -l
```
and post the output.

---

### Post by yancek on 2017-07-14
Ubuntu and many other Linux operating systems make external drive partitions available under the /media or /media/username direcxtory.  Have you looked there?  Did you format with a Linux filesystem?  Suggestions you will get will be based on your having only Ubuntu installed and no other OS so if that isn't correct, you need to indicate that.  Also, which release of Ubuntu is this?  It should show that on the screen when you boot.

---

### Post by xanderforrest on 2017-07-15
It's ubuntu 17.04. Where is the /media file? Lots of people say that and I don't understand it.

---

### Post by xanderforrest on 2017-07-15
```
Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4         boot




Model: ATA WDC WD1001FALS-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start  End  Size  File system  Name  Flags
```


At the moment the only drives are my 2tb and the 1tb which I can't access

```
sudo mount /dev/sdb /media/
[sudo] password for xander: 
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```


This is what happens when I try to mount my drive.

So I've tried to fix that error by installing nfs stuff and cifs util but nothing is working.

---

### Post by deadflowr on 2017-07-15
It seems to only see one 1TB drive.
see what
```
sudo lshw -c disk
```
shows

(for what it's worth: on the single 1TB drive that it does show there are no partitions.
Probably because Disks doesn't do a good job of creating them.
Ubuntu's Files program, from what I remember, doesn't do a good job of showing whole drives, but rather shows partitions.
It's better to use a program such as gparted, that can actually create a partition table, in my opinion.
but that's just food for thought, if that makes any sense...)

---

### Post by oldfred on 2017-07-15
If you just formatted drive, it is seen as a super floppy and many Linux tools do not work or work well with that. That must see a partition table either the 35 year old MBR or the newer gpt type.

Drives, like sda, sdb, sdc need to be partitioned, even if just one large partition (not always recommended) and then the partitions are formatted. Partitions are then seen as sda1, sda2, sdb1 etc.

I use gpt and include both an ESP (for UEFI boot) and a bios_grub partition as first partitions, even on data only drives. So if in future I want to put an install on that drive, do have have to totally redo partitions. 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT

[/URL]
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

[URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]
[/URL]

---

### Post by yancek on 2017-07-15
> It's ubuntu 17.04. Where is the /media file?

It's not a file it is a directory or folder.  The link below explains the filesystem hierarchy.  If you know how to open a filemanager such as nautilus, click the up arrow until you see the various directories in the root of the filesystem.

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

As pointed out in comments above, the standard procedure is to create a partition and then format with a Linux filesystem on the partition.

---

### Post by johndough2 on 2017-07-16
Hi

Lots of good advice given.

I think the problem is that you have not listed the drives that you have, so a little precis....

You have 1 large partition of 2 Tb on /dev/sda?

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4         boot

and presumably it works with the Linux Format install of Ubuntu Unity.

Then you added, internal?, drives 2 x 1Tb and they are not showing anywhere that is useful to you, am I right so far?

##############################################

If so they should be /dev/sdb and /dev/sdc respectively.

When you partition and format them you will have /dev/sdb1 and /dev/sdc1 respectively.

You cannot expect to mount them until they have a designation, sometimes the mount is automatic and not necessarily the same for every linux out there.

johndough@LAPTOP:/$ ls
bin  boot  cache  data  dev  etc  home  init  lib  lib64  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var


You can see the listing of my / (cd /)  then I would type 

johndough@LAPTOP:/$ cd /media
johndough@LAPTOP:/media$ ls
johndough@LAPTOP:/media$

and find my /media directory is empty, much like my skull.

So the first step is too create the /dev/sdb1 and /dev/sdc1 partitions, and I would go with Gparted and make them NTFS personally because if I got in a strop and went back to windows they would be readable, probably.

So please tell us what you know or find difficult to follow in all of the wise words above, including mine  arf arf.

If in doubt please ask.

---

