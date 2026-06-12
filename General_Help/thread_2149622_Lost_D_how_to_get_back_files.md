---
title: "Lost D: how to get back files?"
date: 2013-05-29
forum: General Help
---

### Post by dhruvdangi on 2013-05-29
I had windows 8 installed on my dell inspiron m5010 and had 4 partitions of which 1 was made for dell, 1 for windows 8 and 2 others(150mb and 100gb)
While installing ubuntu 13.04 i clicked on somthing else as i wanted to dual boot, then i choose the 100gb partition and ext4, and not to format it and then installed it.
then after installation i rebooted but ubuntu was not booting so i again booted through the live Pen drive and then installed some boot repair and now it is working file.
but now i dont know where is my D: , in windows now there is only c: and a system partition.
I need to access the files in it but i have no clue what to do.
please help

---

### Post by grahammechanical on 2013-05-29
You will not have a D: drive in Linux. The Ubuntu file manager will show you devices which will be either hard drives or the partitions on the hard drives and they will be labelled with their sizes. What partition was the D: drive under Windows? Was it by any chance the 100GB partition? If so then you have installed Ubuntu over that data.

Perhaps you have made a typing mistake when you describe a partition as 150mb. Perhaps it is really 150GB and that is where the data is. In Ubuntu it is not called D: or C: or anything like that.

Regards.

---

### Post by Grenage on 2013-05-29
The boot repair may simply have overwritten your boot records; post the output of:

```
sudo fdisk -l
```

---

### Post by dhruvdangi on 2013-05-29
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3c19760


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2         4276224   213991423   104857600   83  Linux
/dev/sda3   *   213991424   214196223      102400    7  HPFS/NTFS/exFAT
/dev/sda4       214196224   625139711   205471744    7  HPFS/NTFS/exFAT
dhruv@Dhruv-Inspiron-M5010:~$ 

@[COLOR=#000000]grahammechanical I have no clue on which drive i have installed ubuntu all i can say that while installation i choose DO NOT FORMAT, so why will ubuntu format the drive?And in any case is there any way i can recover the files?
sda2 is where i installed ubuntu 13.04[/COLOR]
and the sda3 is windows 8
i have no clue about sda4 and i have no other Operating system installed

---

### Post by CatKiller on 2013-05-29
You can't change NTFS into ext4 without formatting.

---

### Post by dhruvdangi on 2013-05-29
So there is no way i can get back my files??

---

### Post by dino99 on 2013-05-29
[http://www.easeus.com/partition-recovery/](http://www.easeus.com/partition-recovery/)
[http://www.securitytube.net/video/4411](http://www.securitytube.net/video/4411)

---

### Post by Mark Phelps on 2013-05-29
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

