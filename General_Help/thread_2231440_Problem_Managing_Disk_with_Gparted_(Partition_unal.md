---
title: "Problem Managing Disk with Gparted (Partition unallocated) Outside of disk error"
date: 2014-06-25
forum: General Help
---

### Post by vw16v on 2014-06-25
I was trying to free up some space on my dual boot linux / windows xp system today and managed to hose things up! 

I was frequently running out of space on my 80 gig drive where I have xubuntu installed on one of the partitions. So, I figured I would try and use gparted to free up resize my /home directory on my sdb drive.

Here's my disk layout when everything was fine before I did anything. I have two 80gig hdd's installed in this system. I have windows xp installed on my sda drive. And linux is installed on sdb. The boot manager/grub in on sda boot partition. 

Here's my Partitions Before they Got Messed Up.
    Forum: [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")

 
```
sudo fdisk -l 

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16126    78145535    39064705    f  W95 Ext'd (LBA)
/dev/sdb2        78145536   156301311    39077888   83  Linux
/dev/sdb5           16128    75167845    37575859    7  HPFS/NTFS/exFAT
/dev/sdb6        75169792    78145535     1487872   82  Linux swap / Solaris

df -k
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sdb2       38464148 32660128   3850128  90% /
udev              243428        4    243424   1% /dev
tmpfs              50792     1352     49440   3% /run
none                5120        0      5120   0% /run/lock
none              253948      156    253792   1% /run/shm
```

 Now, gparted doesn't even see my partitions on the sdb disk where my linux resides!!! This is where I was trying to free up some space and extend my home directory.
 In the process I managed to causes problems with my sdb load partition layout and swap file. 

What I did to try and free up more space on the same 80gig sdb drive was boot into my windows xp load and moved all the data off /dev/sdb5 onto my sda drive where my windows xp load is on another 80 gig drive. I then deleted this parition using windows disk manger and windows shows the 30  + gigs as unallocated/unused. 

Now, when I go into gparted it thinks the entire sdb drive is unallocated space! It has and error symbol on the partition and when I click on info it says warning "Can't have partition outside the disk". See pictures below.

Here's my sda disk where my windows xp resides.
[IMG]http://home.comcast.net/~16v/ubuntu/sda.png[/IMG]

Here's where my linux load is and where my swap /root /home should be>
[IMG]http://home.comcast.net/~16v/ubuntu/sdb.png[/IMG]

And the error>
[IMG]http://home.comcast.net/~16v/ubuntu/sdberror.png[/IMG]

I'm still able to boot into windows xp and my xubuntu but I'm unable to manage or use the 36gigs I free'd up in windows since I can't manage or see the disk in gparted. This has also messed up my swap file and I don't have a swap disk anymore. I definitely need my swap disk on this old system! 

Now my partitions are showing the following>

```
john@home:~$ sudo fdisk -l -u /dev/sdb
omitting empty partition (5)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x541ef9d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16126    78145535    39064705    f  W95 Ext'd (LBA)
/dev/sdb2        78145536   156301311    39077888   83  Linux
/dev/sdb5       712786111   188576446  1885378816   ea  Unknown


df -k
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sdb2       38464148 32655960   3854296  90% /
udev              243428       12    243416   1% /dev
tmpfs              50792      896     49896   2% /run
none                5120        4      5116   1% /run/lock
none              253948      156    253792   1% /run/shm
/dev/sda3        5039616    10008   4773608   1% /media/8bea208f-eecc-4a57-b1c9-0b94234505cc
```

I'm trying to fix this issue. I came across this article after searching partition outside of disk error.

[http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk](http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk)

Since my /dev/sda5 where I deleted the partition in windows is now outisde the disk size at 156301488 sectors I'm wondering how to proceed???

/dev/sdb5       712786111   188576446  1885378816   ea  Unknown


I'd like to recover so I can see the partition in gparted again and manage my swap and hopefully use the 36 gigs I free'd up in windows. 

But when I was following the article to backup my current sdb config before trying to resize those blocks I got another error>

```
john@home:~$ sudo sfdisk -d /dev/sdb > ~/Documents/sdb-backup.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

```


Sorry for the long post but it's been a long work night/day. 

I think part of the issue is gparted didn't like me deleting the windows partition on /dev/sdb5 since the swap file came after on /dev/sdb6. I also noticed some sort of uuid disk error or something when ubuntu boots. Either way, I hosed it up and would greatly Appreciate any/all help! Surprised it's even working now!

   Edit. I just booted into windows to take another look. It still shows the 30+ gig partition I deleted on Disk 1 as unallocated. And it shows 339GB of free space where my swap file used to be! I don't know how this happened and why it thinks that since this is only an 80 gig disk. It also show the disk size wrong for disk 1. It should match disk 0 and show 74 gb. 

I wish I would have taken screen shots of disk manager and gparted before this happened. Thx again for any help before I try resizing sectors,etc.

Here's a shot of windows disk manager.

[IMG]http://home.comcast.net/~16v/ubuntu/windowspartition.JPG[/IMG]

---

### Post by coffeecat on 2014-06-25
I think this might help:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by oldfred on 2014-06-25
Do not use Windows tools to delete partitions, use gparted. Windows does not correctly see Linux partitions especially if logical, and regularly rewrites new partition table without the Linux partition.
You may be able to use testdisk to restore Linux partition.
If you need to change partitions from primary to logical or repair structure, then coffeecat's suggestion of fixparts is better.

The cylinder boundary error has not applied for years. Not sure why it still shows it. Drives have not used cylinders since they went over 8GB and converted to LBA or large block allocation. But new drives do need to be on 1MiB boundaries.

---

### Post by vw16v on 2014-06-26
Hey guys, I greatly appreciate the responses! I'm going to look into the testdisk and possibly fixparts utility now to see if I can get this corrected!

oldfred, I learned the hard way not to delete partition in windows! I was assuming I could just boot back into linux and happily extend my /home partition with the space I free'd up. Not so!

I'm on a really old Pentium III 600Mhz system with older harddrives but they are 80gigers so not sure about the cylinders. 

I'm in windows now and this is what diskpart shows for my Disk 1>

Disk 1 is now the selected disk.

DISKPART> list partition

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Extended            37 GB  8063 KB
  Partition 2    Logical           1798 GB   340 GB
  Partition 3    Unknown             37 GB    37 GB


DISKPART> detail partition

Partition 2
Type  : EA
Hidden: Yes
Active: No

There is no volume associated with this partition.

I'm going to back up critical files before I continue and will post back. Thanks again!

---

### Post by vw16v on 2014-06-26
> **oldfred said:**
> Do not use Windows tools to delete partitions, use gparted. Windows does not correctly see Linux partitions especially if logical, and regularly rewrites new partition table without the Linux partition.
You may be able to use testdisk to restore Linux partition.
If you need to change partitions from primary to logical or repair structure, then coffeecat's suggestion of fixparts is better.

The cylinder boundary error has not applied for years. Not sure why it still shows it. Drives have not used cylinders since they went over 8GB and converted to LBA or large block allocation. But new drives do need to be on 1MiB boundaries.

Hello [COLOR=#000000]oldfred, I just installed testdisk and I believe this can fix my issue. Testdrive shows the correct capacity for the drive at 74GB. Also, it still sees all my old partition names and appears it can recover them. The only one I deleted in Windows is called BIGDADDY. It sees my swap file and [/COLOR][COLOR=#000000]BIGDADDY so that's good news![/COLOR][COLOR=#000000]

Testdisk shows issue on sdab>
[/COLOR]Bad relative sector.
Space conflict between the following two partitions
 1 E extended LBA             1   0 62  4864  85 21   78129410
 5 L Sys=EA               44368 225 17 279087 175 63 3770757632

Can you Advise me if I should proceed with the "Write" to the filesystem/disk?

Here's my output from testdrive. Thanks for any input!

```
TestDisk 6.13, Data Recovery Utility, November 2011Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sdb - 80 GB / 74 GiB - CHS 9729 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors


 1 E extended LBA             1   0 62  4864  85 21   78129410
 2 P Linux                 4864  85 22  9729  78 13   78155776
No partition is bootable
   X extended              4679  25 20  4864  85 21    2975807
 5 L Sys=EA               44368 225 17 279087 175 63 3770757632


Bad relative sector.
Space conflict between the following two partitions
 1 E extended LBA             1   0 62  4864  85 21   78129410
 5 L Sys=EA               44368 225 17 279087 175 63 3770757632


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
>[Quick Search]  [ Backup ]
                            Try to locate partition


I clicked on Quick Search > Next Screen>






TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sdb - 80 GB / 74 GiB - CHS 9730 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              1   1  1  4678 250 13   75151705 [BIGDADDY]
 P Linux Swap            4679  26 20  4864  85  5    2975728
 P Linux                 4864  85 22  9729  78 13   78155776


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 38 GB / 35 GiB




I Clicked Continue>


TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sdb - 80 GB / 74 GiB - CHS 9730 255 63


     Partition                  Start        End    Size in sectors


 1 * HPFS - NTFS              1   1  1  4678 250 13   75151705 [BIGDADDY]
 2 P Linux Swap            4679  26 20  4864  85  5    2975728
 3 P Linux                 4864  85 22  9729  78 13   78155776


 [  Quit  ] >[Deeper Search]  [ Write  ]
                          Try to find more partitions



```

---

### Post by vw16v on 2014-06-26
Shoot!!! I decided to write the partition information that testdisk discovered and after rebooting GRUB doesn't see anything. Can't see either Windows XP or Linux!! I knew I should have waited or tried fixparts instead!

Now, I"m trying to see if I can get a grub fix utility to see if that works to get me booting again.

---

### Post by vw16v on 2014-06-26
Hey guys. My xubuntu load got lost after I tried the testdisk utility!!

I'm super bummed out I hosed my sweet xubuntu load that I've loved running for years!!

I downloaded and installed the boot-repair 32 bit utility. I ran that and it said it repaired my MBR.

I'm now able to boot into windows and I see the BIGDADDY partition I deleted since fixparts recovered that.

However, my Disk1 no longer shows my linux load. :mad:

So, I should have used fixedparts for my issue but it's too late! Here's what Windows XP shows now. I'm going to allocate the entire Disk1 to linux this time so I don't have a space issue. At least I got most all the data backed up that I wanted. 

Thanks for the help and lesson learned. I think.. LOL. *sigh*

Ignore the fact that it shows BIGDADDY as my C: drive. My bootable drive is E: for windows on DISK 0. That got messed up a while back and I didn't mess with it. 

[IMG]http://home.comcast.net/~16v/ubuntu/windowspartitionjacked.JPG[/IMG]

---

### Post by coffeecat on 2014-06-26
oldfred has mentioned something about this, but you cannot trust the Windows Disk Management Utility to show your partition layout accurately when there are Linux partitions, particularly logical ones. You need to boot up with a (x)ubuntu live disc and see what Gparted is telling you. Post a screenshot of the Gparted window.

---

### Post by vw16v on 2014-06-26
> **coffeecat said:**
> oldfred has mentioned something about this, but you cannot trust the Windows Disk Management Utility to show your partition layout accurately when there are Linux partitions, particularly logical ones. You need to boot up with a (x)ubuntu live disc and see what Gparted is telling you. Post a screenshot of the Gparted window.

Right, good point coffeecat! Cool name BTW! I'm going to try and boot off my Ubuntu 12.04 disk VIA CD. This old system won't even let me boot of my USB sticks! So, I'm stuck with Floppy and CD ROM to try and recover. At least I'm back in Windows for now.  

I'll report back after I boot up off a live CD and then go into gparted to see what it shows. Thanks again for the help!! Don't want to wipe this disk yet. I did delete my BIGDADDY windows partition off it again since I don't want/need that data or partition anymore.

---

### Post by vw16v on 2014-06-26
Hi Guys, I think I'm going to have to try and reload my Xubuntu. I booted off a 12.04 Ubuntu CD I have and started gparted.

gparted now see's the partitions but it looks like my linux is gone? Any other suggestions before I do a reload? Thanks again.

Here's what gparted shows now for sdb drive.

[IMG]http://home.comcast.net/%7E16v/ubuntu/gpated.png[/IMG]

---

### Post by oldfred on 2014-06-26
Please post screen shots as attachments not in line. You can easily do that with Go Advanced editor and use the paperclip icon.

Not sure you have partition structure correct. And if not correct gparted does not show anything.

Post this:
sudo parted -l
sudo fdisk -lu

The logical partitions must all be inside the extended partition or when reassigning in testdisk, all logicals must be next to each other so it has only one extended. And extended counts as one of the 4 primary partitions.

---

### Post by vw16v on 2014-06-26
> **oldfred said:**
> Please post screen shots as attachments not in line. You can easily do that with Go Advanced editor and use the paperclip icon.

Not sure you have partition structure correct. And if not correct gparted does not show anything.

Post this:
sudo parted -l
sudo fdisk -lu

The logical partitions must all be inside the extended partition or when reassigning in testdisk, all logicals must be next to each other so it has only one extended. And extended counts as one of the 4 primary partitions.

Hi oldfred. Ok, I'll post attachments. Thanks for that info. Here's my output from these commands. I'm almost sure my linux still resides on my extended partition on sdb. It's just a matter or recovering it somehow. Not sure if I should attempt the fixparts tool or something? Thanks for any suggestions. I'm kinda tired. 

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST380011A (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  41.9GB  41.9GB  primary   ntfs         boot
 3      41.9GB  47.2GB  5243MB  primary   ext2
 2      47.2GB  80.0GB  32.8GB  extended


Model: ATA ST380011A (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      8225kB  38.5GB  38.5GB  extended               lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

Error: /dev/zram0: unrecognised disk label                                

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x484d5754

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS/exFAT
/dev/sda2        92155904   156301311    32072704    5  Extended
/dev/sda3        81915904    92155903     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x541ef9d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065    75168134    37576035    f  W95 Ext'd (LBA)
ubuntu@ubuntu:~$ df
Filesystem     1K-blocks   Used Available Use% Mounted on
/cow              253800  52016    201784  21% /
udev              246168      4    246164   1% /dev
tmpfs             101524    700    100824   1% /run
/dev/sr0          718124 718124         0 100% /cdrom
/dev/loop0        688256 688256         0 100% /rofs
tmpfs             253800     16    253784   1% /tmp
none                5120      4      5116   1% /run/lock
none              253800     76    253724   1% /run/shm
ubuntu@ubuntu:~$ 


```

---

### Post by oldfred on 2014-06-26
I think fixparts only resets existing partitions or lets you convert logical & primary within the allowed partition rules. But does not find missing partitions.
 Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

 
It now looks like you have more missing partitions. In testdisk did you click to include all the partitions you wanted?

You may be able to use the sdb-backup.txt to restore and then try again with testdisk or parted to restore the missing partition.

 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

Or if you know exact sector starts & ends you can add them to your sdb-backup.txt and restore that. The backup is just a text file with info on start &  size of partition. It uses start & size where others use start & end so you have to do some calculations.

       Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by vw16v on 2014-06-28
Hi oldfred, Thanks again for your help on this. However, ever since I went into testdisk and "Wrote" the file system I haven't been able to see those linux partitions anymore. I think I should have tried fixparts to correct the partition in windows is now outisde the disk size issue.

I did mess around with fixparts again last night but it's not seeing the linux partitions anymore and I'm pretty sure I'm beyond recovery. It's too bad since this system was running for years and I corrected obscure xfce panel issues and lots or other problems but this is the final bullet in my xubuntu load. I will be loading it from scratch again. 

I suppose if I would have used gparted to delete the windows partition in the first place I never would have ran into this problem.

---

### Post by vw16v on 2014-07-04
Closure, I just wanted to report back and say I got my xubutu working again after a fresh reload. This time I didn't leave any windows partitions on my 2nd hard disk (sdb) that I loaded it on. I used the whole disk for linux. I had to find an older 12.04 version to load that would fit on a CD but that was the only issue.  It noticed my Win XP load and loaded Grub to sda and dual boot still works fine. 

I'm currently going through all my tweaks and config changes to help lock it down a little. That's the main reason I didn't want to reload. I have lots of various tweaks I do and that takes a while. Configuring ufw is kinda fun. 

I wish I would have been able to recover from my mistake of deleting the windows partition in XP and booting into linux but after "writing" the MBR/file system that testdisk discovered I bricked my load bad. 

If someone makes this mistake like I did I would advise trying fixparts as opposed to testdisk. Either way, it's kinda nice to have a fresh load with all this space. Xubuntu Rocks on older systems! 

Thanks again oldfred and coffeecat. ):P

---

