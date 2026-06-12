---
title: "Dual Boot ubuntu fails to boot after expanding ubuntu partion"
date: 2012-12-23
forum: General Help
---

### Post by Dabo Ross on 2012-12-23
Basically this is what happened. 

I installed ubuntu 12.04 with windows 7. As a dual boot. It has worked perfectly in the past, with selecting which operating system to boot into with the windows boot loader.
That is, until I decided I needed more space on my ubuntu drive.
I previously had a 500gb C: drive, and a 20gb ubuntu drive, which, frankly, isn't enough if I am regularly using ubuntu.

I booted into a Live ubuntu cd tonight, and I used gparted to shrink my windows 7 partion by around 50gb, and "shift left and extend" my ubuntu partion to encompass this space. 
After doing this when I rebooted my computer, I could not boot into ubuntu, and the windows boot loader gave me an error saying that "windows failed to start." and the file /ubuntu/winboot/wubildr.mbr was missing or corrupt. (I can't remember the exact words it used"

I went into the Live CD again, and this time running the boot repair program, and it did not help.
I next decided to boot into windows 7. Windows insisted on checking all the disks for corruption, but after it did that it booted fine. I am using it right now.
But I still get that error when I boot into ubuntu.

I am pretty sure that this has been posted somewhere in the past, but with searching and Google, I can not find anyone in my situation. 

I can access the files in my Ubuntu drive from windows, and from a live CD, so if I need to I can just copy all of them over into windows, and then remove and re install ubuntu.
I would prefer to not have to re install ubuntu if I do not have to though.

I guess I am looking for a way to fix this error. If you can help, thank you.

EDIT: Another question, is my install of ubuntu consider wubi? I have it dual booting with windows using the windows bootloader.
Also would installing grub fix this problem? And would grub also be able to boot windows 7?

EDIT: After finding more info, I realize that I do have WUBI, and that I think I want to uninstall and re install using the conventional installer. I hope that will fix my issue.

---

### Post by fdrake on 2012-12-23
wubi runs in windows so just boot in win and uninstall wubi... ta...da!!!

get a live usb/cd of 12.04 and install with the pre-deffined configuration "install ubuntu with windows". then you will be able to boot into a the real partition.. google around for more info... there are plenty.

---

### Post by Dabo Ross on 2012-12-23
> **fdrake said:**
> wubi runs in windows so just boot in win and uninstall wubi... ta...da!!!

get a live usb/cd of 12.04 and install with the pre-deffined configuration "install ubuntu with windows". then you will be able to boot into a the real partition.. google around for more info... there are plenty.

I do actually have ubuntu in a seperate partion though, if I read gParted correctly...
as I said in my post I have used a liveCD to try to fix it, and to expand the partion.
Currently I am in that liveCD backing up my data so that I can remove it and re install using this live CD.

---

### Post by fdrake on 2012-12-23
> **Dabo Ross said:**
> I do actually have ubuntu in a seperate partion though, if I read gParted correctly...
as I said in my post I have used a liveCD to try to fix it, and to expand the partion.
Currently I am in that liveCD backing up my data so that I can remove it and re install using this live CD.
 with the live cd in the terminal run "sudo parted -l" or "sudo fdisk -l". just press enter if it ask  for a pass.. paste here the output.

---

### Post by Dabo Ross on 2012-12-23
> **fdrake said:**
> with the live cd in the terminal run "sudo parted -l" or "sudo fdisk -l". just press enter if it ask  for a pass.. paste here the output.

Last time I used fdisk -l when I was trying to expand ubuntu It came up with 6 partions. I would rather not go back into live CD again at the moment, currently I am logged into windows. 
I have 3 partions that seem to be windows, and then a backup drive, and ubuntu partion. I will go into live CD now and get the exact output of the command.

EDIT: > **fdrake said:**
> wubi runs in windows so just boot in win and uninstall wubi... ta...da!!!

get a live usb/cd of 12.04 and install with the pre-deffined configuration "install ubuntu with windows". then you will be able to boot into a the real partition.. google around for more info... there are plenty.

I just tried using the Ubuntu uninstaller, and it seems to work, but then windows checks if "this program was installed correctly"...
and the ubuntu drive is still there...

Do you think it would harm my computer just to format the ubuntu partion?

EDIT 2:
Here is the result of those commands:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe2a07366

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    42485759    21201920    7  HPFS/NTFS/exFAT
/dev/sda3        42487808  1006723071   482117632    7  HPFS/NTFS/exFAT
/dev/sda4      1006723072  1465147391   229212160    f  W95 Ext'd (LBA)
/dev/sda5      1006725120  1300326399   146800640    7  HPFS/NTFS/exFAT
/dev/sda6      1300328448  1465147391    82409472    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD7500BPKT-7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16        diag
 2      41.9MB  21.8GB  21.7GB  primary   ntfs         boot
 3      21.8GB  515GB   494GB   primary   ntfs
 4      515GB   750GB   235GB   extended               lba
 5      515GB   666GB   150GB   logical   ntfs
 6      666GB   750GB   84.4GB  logical   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           


```Also, sorry for not being appreciative, I am thankful that you replied so quickly. I am just not in the best of moods, mostly as a result of trying to figure all this stuff out.


Also, according to GParted, 

sda1 is "DellUtility"
sda2 is "RECOVERY"
sda3 is "OS", windows 7 I am assuming. 
sda5 is a backup drive I created.
sda6 is the ubuntu drive
also, sda1 is fat16
sda2,3,5, and 6 are ntfs.
and sda4 is "extended". I am assuming windows created sda4 so that I could have more then 4 partions.
there is a 1MiB unallocated section between sda2 and sda3.
[http://i48.tinypic.com/1orwjq.png](http://i48.tinypic.com/1orwjq.png) is a screenshot of GParted.

---

### Post by Dabo Ross on 2012-12-24
I have basically fixed this issue by completely removing the Ubuntu partion after backing up my data, and re installing through a live CD. Thank You.

---

