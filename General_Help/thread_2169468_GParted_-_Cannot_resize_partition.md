---
title: "GParted - Cannot resize partition"
date: 2013-08-22
forum: General Help
---

### Post by FotisGR on 2013-08-22
Hi,

My current partitions:

[ATTACH=CONFIG]245583[/ATTACH]

sda1 is windows partition.
sda2 is ubuntu partition.

I want resize sda2 using the unallocated size of sda1, but i receive this error.

[ATTACH=CONFIG]245584[/ATTACH]

Of course i try to resize the partitions via bootable usb with ubuntu.

Why i get this error?

Thank you.

---

### Post by Quackers on 2013-08-22
Interesting. Can you tell me what shows up if you click on the little black arrow next to "libparted messages" in your second screenshot (near the bottom left of the window)?
Also in order to resize sda2 did you click on it and then drag the partition to the left?

Incidentally sda2 is an extended partition (like a box) which holds sda5 which is your Ubuntu partition.

---

### Post by FotisGR on 2013-08-22
> **Quackers said:**
> Interesting. Can you tell me what shows up if you click on the little black arrow next to "libparted messages" in your second screenshot (near the bottom left of the window)?
[ATTACH=CONFIG]245586[/ATTACH]

> **Quackers said:**
> 
Also in order to resize sda2 did you click on it and then drag the partition to the left?

Right click - resize 
[ATTACH=CONFIG]245588[/ATTACH]
[ATTACH=CONFIG]245587[/ATTACH]

> **Quackers said:**
> 
Incidentally sda2 is an extended partition (like a box) which holds sda5 which is your Ubuntu partition.

Hmmm, is this problem?

---

### Post by Quackers on 2013-08-22
In your last screenshot it appears to be waiting for you to click on the green tick near the top of the page. If you click on that it should run.
If that goes ok do the same for sda5 so that it fills the extended partition completely (sda2).

No, it shouldn't be a problem that you have a logical partition (sda5) inside an extended partition (sda2).

The earlier message about overlapping partitions is a concern though.

---

### Post by FotisGR on 2013-08-22
> **Quackers said:**
> In your last screenshot it appears to be waiting for you to click on the green tick near the top of the page. If you click on that it should run.


When i click the green tick this appears.

[ATTACH=CONFIG]245586[/ATTACH]

---

### Post by Quackers on 2013-08-22
I see thanks. There may be something wrong with your partition table - or possibly your extended partition.
Are you booted into a live cd/usb Ubuntu desktop?
If so please open a terminal and type
[HTML]sudo fdisk -l[/HTML]
and paste the output in your next post using code tags.
(The -l at the end is a lower case L not a 1)

---

### Post by FotisGR on 2013-08-22
```

ubuntu@ubuntu:~$ sudo fdisk -l 


Disk /dev/sda: 128.0 GB, 128035676160bytes 
255 heads, 63 sectors/track, 15566cylinders, total 250069680 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes /512 bytes 
Disk identifier: 0xe5abc1ba 


   Device Boot      Start         End     Blocks   Id  System 
/dev/sda1   *        2048   188637183   94317568    7  HPFS/NTFS/exFAT 
/dev/sda2       210063358   250068991   20002817    5  Extended 
/dev/sda5       210063360   250068991   20002816   83  Linux 


Disk /dev/sdc: 8006 MB, 8006926336bytes 
255 heads, 63 sectors/track, 973cylinders, total 15638528 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes /512 bytes 
Disk identifier: 0x002c3cf0 


   Device Boot      Start         End     Blocks   Id  System 
/dev/sdc1   *        2048    15638527    7818240    c  W95 FAT32 (LBA)  

```

---

### Post by Quackers on 2013-08-22
Thanks. I'm not sure whether anything is wrong with that output. 
I have asked another member to take a look and see whether I have missed anything.

---

### Post by oldfred on 2013-08-22
I do not see anything wrong either.
But to be safe lets back up partition table and save file to external device.
Post file, but it really is the same as your fdisk, but different format.

 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

We can do it manually with sfdisk by editing the above text file. But I would like to know what gparted is seeing that seems to be the issues. The sector numbers do not look like they are overlapping?? Normally gparted also would show other errors, they were an issue.

What version of gparted? If the one from Ubuntu installer and even if recent I might download the newest with either parted magic or gparted itself. I like to have them anyway as backup repair tools.

      
 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by Quackers on 2013-08-22
As already stated I'm not sure that there is anything wrong but there is a utility called Fixparts which was written by a former member of this forum. Just running Fixparts will re-write the partition table and fix any possible problems with the boundaries of the extended partition. I suggest you download and run that utility. It has fixed my partition problems before.
The instruction page is here
[http://www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")
and you can download the utility here
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/")

Follow the instructions and once completed try and run the gparted changes again. Please let us know what happens.

---

### Post by oldfred on 2013-08-22
Fixparts may also give a different set of errors if it something else.

Some of the issues.
 Other partition issues, left over gpt backup partition table data, left over RAID meta-data, partitions needing file check  e2fsck for ext linux family. Windows converting to dynamic disks or Windows needing chkdsk or has hibernation flag set. Some we see with fdisk or gdisk output, others may be hidden and not seen.

---

### Post by FotisGR on 2013-08-24
Finally, i re-install Ubuntu.
I deleted the partition and i create a new 30 giga one.

Thank you for your help.

---

