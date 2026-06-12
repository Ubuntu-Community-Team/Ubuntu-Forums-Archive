---
title: "How do I replace XP with W7 or W8 without losing Ubuntu?"
date: 2014-04-19
forum: General Help
---

### Post by 9k0aefbmMtuJ on 2014-04-19
My laptop has 3 partitions and I have dual boot XP and Ubuntu 12.04 LTS with a separate /home partition. I need a Windows system to run Netflix and two Windows only medical applications.
 I know that I could wipe my HDD, install W7 or W8 then Ubuntu and restore my /home, or just wipe the XP and Ubuntu partitions and install W7 or W8 then Ubuntu hoping that /home will stilll be kept.
However is it possible to just install W7 or W8 to the partition occupied by XP leaving Ubuntu intact?

---

### Post by Elfy on 2014-04-19
I'd assume that there is an advanced windows partition setup method - there was years ago.

You will have to reinstall grub once you're finished though. 

"Windows 7 setup considers partition management as an advanced task so you'll need to click the Drive options (advanced) link to make those options available." 

[http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html](http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html)

Windows won't recognise the linux partitions.

---

### Post by coffeecat on 2014-04-19
I don't know about Win8, but you can install Windows 7 to a single NTFS partition without the separate 100MB or so boot partition that would be the default with Windows 7. So it is theoretically possible but you would need to take great care with the Windows 7 installer. And it would be a sensible precaution to back everything up in case something untoward were to occur. For example....

The Vista installer, and I am sure this would be true of the Win7 installer, would sometimes delete the first logical partition if there were fewer than 4 primary partitions present. This often meant the Linux root partition. Why? I don't know. All I can say is that I did some experiments with the XP and Vista installers a few years ago, and the results with systems containing Linux logical partitions were hair-raising but not seemingly consistent. Sometimes it happened, and sometimes not. The moral is - exercise great caution when installing Windows to a hard drive with Linux logical partitions. Which leads us to your:

> My laptop has 3 partitions and I have dual boot XP and Ubuntu 12.04 LTS with a separate /home partition.

Unless you have no swap partition, that doesn't quite add up. It might help for you to post the output of this terminal command in Ubuntu so that we can see your partition layout:

```
sudo fdisk -l
```

Also - as Elfy says, the Windows installer will overwrite the mbr and you would have to reinstall grub.

---

### Post by 3rdalbum on 2014-04-19
I did this a slightly different way: I had Windows 8 Consumer Preview on Partition 1, Ubuntu on Partition 2, and then I installed Vista over Windows 8 onto Partition 1 while leaving Ubuntu on Partition 2.

The Windows installer allows you to choose a partition to use. Select your current XP partition. After the installation is finished, your system will only boot into Windows - so boot up an Ubuntu live CD and install the Boot Repair program into the live CD environment. Run Boot Repair on "Recommended" and it will sort out everything for you, and you'll get access to both OSes again.

---

### Post by Elfy on 2014-04-19
Boot repair is not available for Trusty yet - need to edit the source to point at saucy.

---

### Post by 9k0aefbmMtuJ on 2014-04-19
> **coffeecat said:**
> 
Unless you have no swap partition, that doesn't quite add up. It might help for you to post the output of this terminal command in Ubuntu so that we can see your partition layout:

```
sudo fdisk -l
```




Sorry, yes I do have a swap partition as well and thanks for everyones replies.
I've appended the output of sudo fdisk -l with a description of the partitions in ().

> 
mike@msi-cr620:~$ sudo fdisk -l
[sudo] password for mike: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000516b

   Device Boot      Start         End            Blocks            Id  System
/dev/sda1   *        4096        67112959    33554432      7  HPFS/NTFS/exFAT    (Windows XP)
/dev/sda2       100667390   436211711   167772161    5  Extended
/dev/sda5       100667392   167776766    33554687+  83  Linux                        (Ubuntu 12.04)
/dev/sda6       201330688   335548415    67108864    83  Linux                         (/home)
/dev/sda7       369102848   436211711    33554432      7  HPFS/NTFS/exFAT   (shared XP/Ubuntu data)
/dev/sda8       197326848   201326591     1999872      82  Linux swap / Solaris (swap)

Partition table entries are not in disk order

mike@msi-cr620:~$ 



---

### Post by 9k0aefbmMtuJ on 2014-04-19
Thanks 3rdalbum.

That looks like a quick way of doing what I want to do.

Mike

---

### Post by 9k0aefbmMtuJ on 2014-04-19
> **Elfy said:**
> Boot repair is not available for Trusty yet - need to edit the source to point at saucy.

I'm running Precise so maybe no problem. I'll prefer to stick with LTS releases and will install Trusty in my  / partition in due course; maybe in 6 months time.

---

### Post by cecilieaux on 2014-04-19
> **michael-eacott said:**
>  I need a Windows system to run Netflix and two Windows only medical applications.

I'm going through similar problems with the death of XP, but I am trying to avoid Windows at all and you may be able to as well.

In the case of Netflix, which I don't use, I found this video in which Nixie Pixel assures us that Netflix can be installed and run in Linux, see

[http://www.youtube.com/watch?v=Tfte5su5DIA](http://www.youtube.com/watch?v=Tfte5su5DIA)

As for your medical applications, have you considered a virtual machine with Windows XP? I am in the process of doing that to preserve some apps that are mission critical and just don't have good Linux equivalents. Microsoft says it's legal. If you're interested, I'll report on how and why when I finally succeed. I think that's only days away.

Cheerio,
Cecilieaux

---

### Post by coffeecat on 2014-04-19
> **michael-eacott said:**
> 
I've appended the output of sudo fdisk -l with a description of the partitions in ().
```
mike@msi-cr620:~$ sudo fdisk -l
[sudo] password for mike:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000516b

Device Boot Start End Blocks Id System
/dev/sda1 * 4096 67112959 33554432 7 HPFS/NTFS/exFAT (Windows XP)
/dev/sda2 100667390 436211711 167772161 5 Extended
/dev/sda5 100667392 167776766 33554687+ 83 Linux (Ubuntu 12.04)
/dev/sda6 201330688 335548415 67108864 83 Linux (/home)
/dev/sda7 369102848 436211711 33554432 7 HPFS/NTFS/exFAT (shared XP/Ubuntu data)
/dev/sda8 197326848 201326591 1999872 82 Linux swap / Solaris (swap)

Partition table entries are not in disk order

mike@msi-cr620:~$ 
```


This layout is just the situation where the Windows installer might - I emphasise **might** - delete your sda5 partition without warning. You have fewer than the allowed 4 primary partitions, and when this happens the Windows installer sometimes deletes the first Linux logical partition. It's unpredictable so I can't say for certain, but something to bear in mind as a possibility in the context of the other advice you have received in this thread.

---

### Post by oldfred on 2014-04-21
Usually in the cases where Windows deletes a Linux partition, it can be restored with testdisk as it still is there.

But if you have a backup of partition table and do not change partitions, you can easily restore from the backup.

 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

