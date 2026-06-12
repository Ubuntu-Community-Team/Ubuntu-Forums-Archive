---
title: "SATA drive order causing problem at boot up"
date: 2013-04-24
forum: General Help
---

### Post by Steve Francis on 2013-04-24
I have a dual boot p.c. with four SATA hard drives:[INDENT]/dev/sda ...Windows XP installed (one primary NTFS partition 74GB)
/dev/sdb .../media/Video 1 (one primary NTFS partition **750GB**)
/dev/sdc ...Ubuntu 10.04 and extended NTFS partition for data drives (500GB)
/dev/sdd .../media/Video 2 (one primary NTFS partition 1TB)
[/INDENT]

The **750GB drive failed** so I replaced it with a new 2TB Western Digital Green HDD drive which I formatted as one extended NTFS partition.

_**Boot up**_ - When I reconnected the SATA cables following installation of the new drive, the p.c. would boot successfully into XP but **not into Ubuntu 10.04** (the cursor just blinked after entering grub).

I swapped over two of the SATA cables and managed to boot up into Ubuntu, however the following warning appeared.[INDENT][FONT=courier new]The disc drive for /media/Video 2 is not ready yet or not present.
Continue to wait; or Press S to skip mounting or M for manual recovery[/FONT]
[/INDENT]

Once in Ubuntu, if I run Disk Utility, it tells me that
the drive with label Video 2 is mounted at /media/Video 1 and
the drive with label Video 1 doesn't have a mount point

What has caused the problem and **how can I get both media drives to mount automatically at boot up**?

Thanks.

My /etc/fstab looks like this:[INDENT][FONT=courier new]proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=7641d1e1-4d66-402d-a388-6801ca8f2088 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdc4 :
UUID=efbfb084-d04e-4f4c-86b9-c663dded2997 /home ext3 relatime 0 2
# Entry for /dev/sdc3 :
UUID=de59596a-1bf9-41a3-98b9-a2fe09b381f6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdc6 /media/Library ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdd1 /media/Video\0402 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc5 /media/Data ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdb1 /media/Video\0401 ntfs-3g defaults,locale=en_GB.UTF-8 0 0[/FONT]
[/INDENT]

---

### Post by Steve Francis on 2013-04-24
> **Steve Francis said:**
> My /etc/fstab looks like this:[INDENT][FONT=courier new]proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=7641d1e1-4d66-402d-a388-6801ca8f2088 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdc4 :
UUID=efbfb084-d04e-4f4c-86b9-c663dded2997 /home ext3 relatime 0 2
# Entry for /dev/sdc3 :
UUID=de59596a-1bf9-41a3-98b9-a2fe09b381f6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdc6 /media/Library ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdd1 /media/Video\0402 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc5 /media/Data ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdb1 /media/Video\0401 ntfs-3g defaults,locale=en_GB.UTF-8 0 0[/FONT]
[/INDENT]


I've edited fstab so that at least now the label Video 2 corresponds to the mount point /media/Video 2:
[INDENT][FONT=courier new]proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=7641d1e1-4d66-402d-a388-6801ca8f2088 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdc4 :
UUID=efbfb084-d04e-4f4c-86b9-c663dded2997 /home ext3 relatime 0 2
# Entry for /dev/sdc3 :
UUID=de59596a-1bf9-41a3-98b9-a2fe09b381f6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdc6 /media/Library ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sd**b**1 /media/Video\0402 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc5 /media/Data ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sd**d**1 /media/Video\0401 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
[/FONT]
**How do I auto mount Video 1?**

[/INDENT]

---

### Post by Steve Francis on 2013-04-24
```
sudo fdisk -l
```
reports that

[FONT=courier new]<snip>
Partition table entries are not in disk order
<snip>[/FONT]

---

### Post by Steve Francis on 2013-04-24
> **Steve Francis said:**
> [FONT=courier new]Partition table entries are not in disk order[/FONT]

```
[COLOR=#ff0000]steve@mypc:~$ sudo fdisk /dev/sda[/COLOR]
Command (m for help): m
Command (m for help): x
Expert command (m for help): f
Nothing to do. Ordering is already correct.
```

Same for sdb, sdc and sdd. :(

---

### Post by grahammechanical on 2013-04-24
Could it be that the Sata cables have been crossed-over. The motherboard Sata connection are numbered. Sata 1, Sata 2 etc. The BIOS will see the hard drive on the Sata 1 cable as sda but if the hard drive on the Sata 2 cable is the only hard drive then it will be seen as sda. (Yes, I do know that the BIOS cares nothing about sda or hda).

Thankfully, Ubuntu use UUID (Univerally Unique Identifier) for drives and partitions so swapping drives around does not cause too much of a problem.

Can you use the BIOS boot priority to boot into the Ubuntu drive? Once in Ubuntu with all drives in the places you want them to be then run

```
sudo update-grub
``` and ```
sudo grub-install /dev/sdc
```

Make sure that the Ubuntu drive is still sdc. That first command will cause grub to search all the hard drives for operating systems and create an up to date Grub menu. The second command will install Grub into the MBR of sdc. Now if sdc has first boot priority in the BIOS then when you boot the machine the BIOS will look first to sdc for an operating system and find Grub and you will get the Grub menu which has been fixed to correctly point to UUIDs of the Ubuntu and XP partitions. Hopefully.

Regards.

---

### Post by oldfred on 2013-04-24
I have multiple drives and did not put them in SATA port number on hard drive. So sometimes my flash drive fills that drive in order and sometimes it is at the end. Seems to depend on whether flash is plugged in when I boot.

But you really should use UUID for your other drives. The BIOS changing boot order of drives and then device numbers changing was the main reason to use UUIDs which change a lot less.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6


 sudo blkid -c /dev/null -o list
      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

      
 For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

I also prefer not to use spaces in any files, folders, mounts with Linux. Then you do not have the issue of escaping the space or using quotes. I use under_score, CamelCase, or justonelongname.

---

### Post by Steve Francis on 2013-04-24
Thank you, chaps, for your kind replies. After a bit more research, I believe that at least part of the problem is due to buying a Western Digital Caviar Green WD20EARX _with Advanced Format technology_ as my replacement drive. And it seemed like such a good idea at the time! :mad:

> **grahammechanical said:**
> Could it be that the Sata cables have  been crossed-over. The motherboard Sata connection are numbered. Sata 1,  Sata 2 etc. The BIOS will see the hard drive on the Sata 1 cable as sda  but if the hard drive on the Sata 2 cable is the only hard drive then  it will be seen as sda. (Yes, I do know that the BIOS cares nothing  about sda or hda).

This is the case. Unfortunately, when I swap them back to the original 'correct' ports, the p.c. doesn't boot up (in Ubuntu at least. It does boot to XP).

> **grahammechanical said:**
> Thankfully, Ubuntu use UUID (Univerally Unique Identifier) for drives  and partitions so swapping drives around does not cause too much of a  problem.

Can you use the BIOS boot priority to boot into the Ubuntu drive? Once  in Ubuntu with all drives in the places you want them to be then run

```
sudo update-grub
``` and ```
sudo grub-install /dev/sdc
```

Make sure that the Ubuntu drive is still sdc. That first command will  cause grub to search all the hard drives for operating systems and  create an up to date Grub menu. The second command will install Grub  into the MBR of sdc. Now if sdc has first boot priority in the BIOS then  when you boot the machine the BIOS will look first to sdc for an  operating system and find Grub and you will get the Grub menu which has  been fixed to correctly point to UUIDs of the Ubuntu and XP partitions.  Hopefully.

I have made a note of these useful commands. Thanks. I haven't tried them yet because I think that the replacement hard drive is idiosyncratic and Ubuntu doesn't like it.

> **oldfred said:**
> I have multiple drives and did not put them in SATA port number on hard drive. So sometimes my flash drive fills that drive in order and sometimes it is at the end. Seems to depend on whether flash is plugged in when I boot.

But you really should use UUID for your other drives. The BIOS changing boot order of drives and then device numbers changing was the main reason to use UUIDs which change a lot less.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6


Great link. Will do this once I have solved the problem with the rogue replacement drive

 > **oldfred said:**
> sudo blkid -c /dev/null -o list
      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

 For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

Thanks Oldfred for walking me through it.

> **oldfred said:**
> I also prefer not to use spaces in any files, folders, mounts with Linux. Then you do not have the issue of escaping the space or using quotes. I use under_score, CamelCase, or justonelongname.
Yes - following this policy would have made fault finding easier.#-o

---

### Post by oldfred on 2013-04-24
As grahammechanical posted above it just may be BIOS boot order and which drive has grub in the MBR. BIOS defaults to booting from first drive, grub defaults to installing in sda, and moving drives around may change which drive is seen as sda, so it may not have grub2's boot loader in the MBR.
You can change default in BIOS if you know which drive has grub in the MBR, or experiment with one time boot key (f12 on my system but varies).

If you really want to know what is where:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Steve Francis on 2013-04-24
> **Steve Francis said:**
> I believe that at least part of the problem is due to buying a Western Digital Caviar Green WD20EARX _with Advanced Format technology_ as my replacement drive.

Beware Western Digital Caviar Green if, like me, you're unsure about partitioning Advanced Format drives. I read that the beginning of a partition has to be aligned to a 4K sector. :confused:

After much trial-and-error, I had to re-partition and re-format this replacement hard drive.

I used GParted from a live CD to create the new partition. I selected 'Free Space Preceding (MiB)' = 1 and 'Free Space Following (MiB)' = 0. The rest of the space was used for one entire primary partition with a ntfs file format.

Once I had done this I booted into XP and formatted the drive using XP's default allocation unit size. I gave the partition the label Video 1

Now my p.c. will boot up into Ubuntu and XP with no error messages. Exactly as it did before I had the disk failure.

fdisk reports the following for the Caviar Green drive:
```
steve@mypc:~$ sudo fdisk -lu /dev/sdb
[sudo] password for steve:

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00007a85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472    7  HPFS/NTFS
```

Of course, there may yet be performance issues with this drive. I should have researched more thoroughly before I bought it. I've since found quite a good paper and comments on it here: [Linux on 4KB-sector disks: Practical advice]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/")

For now though, the immediate problem is solved so I'll mark this thread accordingly.

---

### Post by Steve Francis on 2013-04-24
> **oldfred said:**
> As grahammechanical posted above it just may be BIOS boot order and which drive has grub in the MBR. BIOS defaults to booting from first drive, grub defaults to installing in sda, and moving drives around may change which drive is seen as sda, so it may not have grub2's boot loader in the MBR.
You can change default in BIOS if you know which drive has grub in the MBR, or experiment with one time boot key (f12 on my system but varies).

If you really want to know what is where:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

You are right, the boot order was incorrect. Happily, I am up and running now. I have posted the link of the working p.c. here: [http://paste.ubuntu.com/5599421/](http://paste.ubuntu.com/5599421/)

The start sector for /dev/sdb1               is 2,048 rather than the default 63. Once I had done this and experimented with swapping SATA cables around, I managed to boot up into the original configuration without needing to edit /etc/fstab 

Thanks for the advice again, oldfred!

---

### Post by oldfred on 2013-04-24
Glad you got it working.

The new default is 2048 for compatibility with your new 4K drives, SSDs and some others.

I believe all this is just more info from the same author as your IBM post above.
 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

