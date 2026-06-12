---
title: "Which version of Ubuntu?"
date: 2013-05-06
forum: General Help
---

### Post by amit2013 on 2013-05-06
Hello people,
I am a newbie in the Field of Linux, I am trying to install Ubuntu parallel to my pre-installed Windows 7 64-bit OS,
Please help me out a little bit here,
To prevent confusion, I am uploading the snapshot of my system Configuration.
So now please tell me Which Version Should i install?

first of all, Is 12.04 is better or 13.04, since, on the Website, it says, that 12.04 has much longer support. (I want to go for the new version, tried but failed to successfully install it.)
also, 

Should i use 64-bit version or 32-bit version?

I want to install Ubuntu in the "L:/" Drive, So would 30GB be fine for Installing UBUNTU?

---

### Post by lykwydchykyn on 2013-05-06
Start with 12.04, it's more tested and probably better for someone new.

You have enough space on that L:\ partition, but keep in mind that Linux uses its own drive formatting so I'd recommend deleting your L:\ drive and just letting Ubuntu set up its own partition on the empty space during installation.

Go ahead and use the 64 bit version, it should be fine.

---

### Post by amit2013 on 2013-05-06
So i should delete my L:/ drive, leave the 30 GB unallocated space, then install Ubuntu in that space, and when the installation is finished, i should merge the remaining unallocated space with my other Drive?? Right??

---

### Post by lykwydchykyn on 2013-05-06
Yes, except the last bit is optional I suppose.  I always like to keep some unallocated space on a drive, since you never know when you might want to try something new.

---

### Post by Impavidus on 2013-05-06
Are those five partitions you now have on a single physical drive or on different physical drives? Because if these are on a single drive and you use MBR partitioning (common for win7) it's possible that Windows converted to dynamic drives, in which case you have a problem.

30GB for Ubuntu is OK. The system needs much less, but you also want to store some files. You can share storage space with windows, as long as you stay clear of the windows C partition.

---

### Post by amit2013 on 2013-05-06
No, I have 3 HDD's, one is 320 GB, 500 GB and 1TB..
My windows is installed in 320 GB one, and I now installed UBUNTU 12.04 in 1TB one,
well, what i did was, i delete the 30 Gb partition of 1TB HDD (here Drive L:\ ) and thn installed ubuntu, then, What i see is in the Windows partition manager, two ext4 File system partitions. one is 4 GB and other is remaining 26 GB..
I have one more question, in ubuntu, its showing that in the properties of home folder, 22 GB free space.. does that mean all the 30 GB that i spared for Ubuntu's installation is used by it, or there is still some unallocated space left?

---

### Post by Bashing-om on 2013-05-06
amit2013; Hi ! My Welcome to the forum .

What I expect to have happened in the install procedure of ubuntu is that the installer set up and also installed a "swap" partition of 4 GB and the operating system is 26 GB. Plenty for starters. By the time you need more you will know more about ubuntu in general and partitioning in particular. No sweat at this time.
in ubuntu to see the partitioning layout; Terminal code:
```
sudo fdisk -l
```[INDENT=2]
hope this helps

[/INDENT]

---

### Post by amit2013 on 2013-05-07
Here's the detail, when i Type "sudo fdisk -l" in the terminal.. 
Is it fine??

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd2903af7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1890609524   945303738+   7  HPFS/NTFS/exFAT
/dev/sda2      1890611198  1953523711    31456257    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1890611200  1945139199    27264000   83  Linux
/dev/sda6      1945141248  1953523711     4191232   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x88149837

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976769023   488383488    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x42d442d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdc2          206848   625137663   312465408    7  HPFS/NTFS/exFAT

---

### Post by Bashing-om on 2013-05-07
amit2013; Hi !

I too do not think the partitioning of the 1TB drive (sda) went well. As depicted in "fdisk's" output:
> /dev/sda1   *        2048  1890609524   945303738+   7  HPFS/NTFS/exFAT
/dev/sda2      1890611198  1953523711    31456257    5  Extended
Partition 2 does not start on physical sector boundary.
I would anticipate IF the sda1 partition ends at block number 1890609524, that the extended partition sda2, to start or be after block number 189060952(5). Looks to me like the sda2 partition is encroaching on the sda1 (Windows) partition.

Others here may have better advise, having greater experience with Window's operating system, but I would :
Remove my logical partitions(sda5 and 6) within the extended partition sda2, and then remove sda2;
Run Windows' check disk utility a couple of times;
Defrag Windows a couple of times;
In Windows make up the unallocated space for the ubuntu install;
In ubuntu's installer -> choose to install ubuntu "along side" the additional operating system and let the install wizard take care of the details.

As an aside one could choose "something else" and manually take charge of the install, setting up the partitions explicitly.[INDENT=2]
that is just the way I see it
[/INDENT]

---

### Post by grahammechanical on 2013-05-07
You made a good choice by installing 12.04 because it has such long term support. If you had installed 13.04 you would have needed to upgrade to 13.10 in six months time and then upgraded to 14.04 six months after that. You can still upgrade in October and next May if you want to but it would be your choice and not forced upon you by the limited support given to 13.04 and 13.10. It is best that those who are new to Ubuntu to use the Long Term Support (LTS) versions. Ubuntu 12.04.2 is the latest LTS.

Regards.

---

### Post by amit2013 on 2013-05-07
Hey, just one more question, Ubuntu on my PC keeps on freezing, sometimes for a minute or sometimes i even had to restart the PC, i didnt thought that I'd be facing this problem, but still.. I dont know what went wrong..
I searched online for its solution, and fount that updating Kernel would help me.. I'm currently downloading the one realesed in april 2013, would it help.. Also, what else should i do to prevent this freezing in future..

---

### Post by amit2013 on 2013-05-07
Hey, one more thing, I am facing a problem with My ubuntu 12.04, It keeps on freezing, so i searched for its solution online, and found out that i need to update my kernel.. well something like that,
so i did so,
when i type "uname -r", in terminam, it was showing 3.5.. something before, now its showing 3.9.0-030900-grneric, Just wanna know if i need to do something else also to prevent this freezing?? 
Although since i installed the new kernal, i haven't faced any such problem, but Its only half an hour since i updated it..

---

