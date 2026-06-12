---
title: "How to safely reduce a Windows partition and increase a Ubuntu one?"
date: 2016-10-10
forum: General Help
---

### Post by Bobby_James on 2016-10-10
I hope this is the correct forum. My question is regarding partitioning. 

I have no less than eight partitions on /dev/sda. They are:

Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system  Name                          Flags

 1      1049kB  524MB  523MB   ntfs         Basic data partition          hidden, diag

 2      524MB   839MB  315MB   fat32        EFI system partition          boot

 3      839MB   973MB  134MB                Microsoft reserved partition  msftres

 4      973MB   316GB  315GB   ntfs         Basic data partition          msftdata (Windows 8)

 5      316GB   473GB  157GB   ext3         Basic data partition          msftdata (Ubuntu)

 6      473GB   499GB  26.2GB  ntfs         Basic data partition          hidden, diag

 7      499GB   500GB  1074MB  fat32        Basic data partition          hidden, diag

 8      473GB   473GB  1049kB                                             bios_grub

I want to reduce the size of /sda4 (Windows 8) and increase the size of /sda5 (Ubuntu 14.04). I infrequently use Windows 8 so there is loads of free disk space. I could decrease /sda4 by 100 GB and increase /sda5 by the same. Of course, I will backup but I would prefer not to harm either the Windows 8 or Ubuntu partitions. 

I realise there are many tools such as Gparted but is there a standard way to safely achieve my goal? Thanks.

---

### Post by Impavidus on 2016-10-10
Boot Windows and use Windows tools to shrink the Windows partition. Reboot Windows a couple of times to let it run all its checks. Then boot from an Ubuntu live disk and use gparted to resize the Ubuntu partition.

---

### Post by SeijiSensei on 2016-10-10
Alternatively you could just mount the Windows partition from Ubuntu and write stuff there.

---

### Post by oldfred on 2016-10-10
I prefer to keep / (root) as a smaller partition. Also with Windows keep c: drive smaller, but has to be a lot larger than Linux /. And with NTFS best to maintain 30% free space inside NTFS partition. At 10% it can get very slow.

I then use /mnt/data for all my data normally in /home as I have multiple Ubuntu versions. Or you can move /home from / into a new partition. And when I used XP, I also had another shared data partition as NTFS, to share Firefox profile, Thunderbird profile & photos.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

      
 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

