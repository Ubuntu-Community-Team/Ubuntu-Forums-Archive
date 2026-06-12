---
title: "Migrating existing partitions to SSD + HDD"
date: 2013-03-19
forum: General Help
---

### Post by memilanuk on 2013-03-19
[COLOR=#000000][FONT=Verdana]I have a Lenovo T530 i5 that I purchased last fall with 4GB ram and a 500GB 7200rpm hard drive, with the intention of upgrading it to 16GB and an 256gb SSD when time/funds allowed. That time is now.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The machine is currently multi-boot Windows 7 Pro, Ubuntu 12.10, openSuSE 12.2 and Linux Mint 14. After a lot of initial fussing around, the latter two get used very little if at all, so I will probably be going to just a dual-boot config. The hard drive is split up with approx. 100GB for Win7, 20GB for each of the Linux distros, 15GB for the Windows recovery partition, 5GB for swap, and the remainder accessible under /srv/data in the various distros.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]When I initially got this machine, the very first thing I did was use clonezilla to image the HDD and store it to a NAS. As I finished doing the various updates, partitioning, more updates, installing other distros, etc. I continued to do periodic images with clonezilla, so I have a pretty good set of backup images that I can go back to for restoration if need be. The user /home directory is backed up using duplicity (Deja Backup) under Ubuntu, also to the NAS.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]What I want to end up with is the SSD as the primary drive, with the Windows system and recover partitions, and Linux partitions as necessary in the remainder, using LVM. The current HDD will be re-purposed and mounted in a caddy in the optical bay under /srv, probably formatted NTFS so its accessible under both Win7 and Linux. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I was thinking of taking another run with clonezilla and imaging the Win7 install, the Ubuntu install, and the /srv/data partition to the NAS one final time. After that... install the new SSD, restore the necessary partitions to it via clonezilla to get Win7 running again, and then re-install Ubuntu from scratch in the remaining space, and restore /home/$user from the NAS using duplicity. The major fly in the ointment here is getting the linux install back to its previous state, as far as installed programs, PPAs, etc.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]What I'm after here is any suggestions as to any glaring faults with the above schema, and ideas on how to get from where I am to where I want to be when all the bits get here.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Monte[/FONT][/COLOR]

---

### Post by oldfred on 2013-03-20
Some have reported clonezilla works, others suggest Windows tools for Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    

You can export a list of installed apps and use that to reinstall all of them. All the data for the apps should be in your /home backup.
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

I think the issue on PPAs is if changing versions as then there may not be a new PPA yet.

 But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

### Post by memilanuk on 2013-03-20
Thanks, the info on backing up and restoring installed packages should prove very helpful.  I'll look into the PPAs as well.

Any ideas on managing the SSD?  Elsewhere people have alluded to some additional concerns being necessary when using them compared to regular spinning HDDs... keeping swap and /tmp off the SSD due to excessive writes, etc?

---

### Post by oldfred on 2013-03-20
There is disagreement on swap. I find with 4GB of RAM I never use it, so the whole issue is moot. But I have swap on my rotating drive and my installs find it. Someone said having some swap is good for a slightly faster boot. Booting looks for swap and has to time out or not find it, so if it finds it, it may boot very slightly faster.

 How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There&#8217;s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.
[http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux](http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux)
Discussion of swap on SSD - best not to)
[http://ubuntuforums.org/showthread.php?t=1937251](http://ubuntuforums.org/showthread.php?t=1937251)

   With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

   [http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)

   fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq]

---

### Post by memilanuk on 2013-03-21
Fred,

Any thoughts on the necessity of overprovisioning the drive by purposely not allocating all the available space to partitions?  It appears that most new drives have ~7% over-provisioning already built in, but I've seen some references to leaving as much as 10-20% unallocated for this purpose...

Thanks,

Monte

---

### Post by oldfred on 2013-03-21
I think it is in the Arch site that they suggest not using more than 70% of a / partition. I know with NTFS & Windows it slows down a lot if down to 10%, but I do not think Linux has that issue. But it may be about SSDs?

         Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by memilanuk on 2013-03-21
Good links, thanks... but (I think) in this case over-provisioning is referring not to limiting how full a given file system is, but reserving a certain amount of drive space (say 25GB as 10% of a 256GB device) to be unused - not part of *any* partition or filesystem - for the purposes of increasing the endurance (longevity) of the device by allowing it to spread some of the write cycles around to reduce the effects of write-amplification as well as being able to work around individual pages that may become defective over time.

[http://www.edn.com/design/systems-design/4404566/Understanding-SSD-over-provisioning](http://www.edn.com/design/systems-design/4404566/Understanding-SSD-over-provisioning)

I get that there is a certain amount (~7%) implicit in the decimal-vs-binary storage size rating of a given device; what I'm fuzzy on is whether its actually necessary to set aside even more space when setting up the partition structure for a new drive - or if any unformatted space would even be used at all by the drive controller.  The linked article appears to be written by someone involved with one particular company, so I'm unclear on what constituted normal practice and what is their marketing hype.

---

### Post by oldfred on 2013-03-21
The decimal vs. binary just means you have less than you really thought you had.

I think Linux reserves 5% in addition to the space automatically used by ext4 file systems for journal. You should leave that , but if just a data partition on one of the new Multi TB drives can easily make it smaller.

 Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdd3


 [http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)
It's the difference between gigabytes (GB) and gibibytes (GiB). One gigabyte = 1000 x 1000 x 1000 bytes (base 10). One gibibyte = 1024 x 1024 x 1024 bytes (base 2).

---

### Post by memilanuk on 2013-03-21
Yes, I know the difference between a gigibyte and a gigabyte.... did you actually read the linked article to see what I was talking about?

---

### Post by oldfred on 2013-03-21
I think I have seen several similar articles, but do not know enough of the technical details to really know if that helps or if it already is done by how the system internally works or not. 
There is even controversy on whether using trim or just scheduling fstrim is better.
 Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

And then which scheduler is better.
I changed to noop per some info a couple of years ago.

 fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 

   noop may not be best scheduler for SSD, deadline may be better
[http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance](http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance)

---

### Post by memilanuk on 2013-03-24
Well... its done... but there are some residual problems.

They don't stem from the SSD itself, but some of the gyrations I had to go thru to get the partitions shrunk and then copied over to the new drive - had to use some Windows software (Macrium Reflect) as things didn't seem to end up bootable when using clonezilla).  Now I have the 256GB SSD as /dev/sda, booting Win7 and Ubuntu 12.10 as planned, with the 500GB 7200 rpm HDD mounted in an UltraBay drive caddy as /dev/sdb - formatted as ntfs (so I can access files stored there from either OS) and mounted under /srv/data in Linux.  After shrinking partitions and cloning them to the SSD, I deleted some other (linux) partitions I had on there, with the intention of expanding the Ubuntu '/' partition (carefully, using a bootable live USB image  rescue 'disc')... but now I'm having issues even seeing any partitions on the SSD inside gparted, and sfdisk -l complains about overlapping partitions.

So now it looks like I'm back to the point of having to back up the partitions to an external drive, reformat the disk and set up the partitions from scratch, and then restore the partitions from the external storage.  Kind of a bummer since things 'seem' to be working otherwise.

The question going thru my mind now is... will backing up and restoring the disk partition by partition (as opposed to a whole-disk image) using clonezilla work, or will the partitions end up overlapping once again after restoration?

---

### Post by oldfred on 2013-03-24
What is the overlapping partition issue. Is it sectors in multiple partitions which is a major issue or one we see where partition labels are wrong and cause issues.
You cannot have a primary partition sda1 thru sda4 inside the extended partition. If that is just the case use fixparts to relabel partitions around. Only if mounting something by device like /dev/sda1 will you require a repair CD to fix fstab or grub.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by memilanuk on 2013-03-24
Originally I had three windows 7 partitions (one for system boot - /dev/sda1, one for the OS - /dev/sda2, and one for recovery - /dev/sda4), which is the way the system was shipped from the OEM.  When I added Linux to the mix, I used an extended partition (/dev/sda4) to contain three 20GB ext4 partitions, one common swap partition, and an ext4 data partition.

I haven't used the other two linux OS installs for a while, so they got deleted as a part of the migration to the SSD.  I also shrunk the data partition considerably.  Both were contained inside the extended partition.

Part of the 'migration' process using Macrium Reflect mandated that I let it resize the partitions on the SSD proportionally to the available space... which made most of them slightly bigger than originally intended.  I really didn't want to do that, but the software wouldn't clone them otherwise.

I moved the remaining data from the old data partition to the new one on /dev/sdb2, and was making the necessary adjustments in /etc/fstab when I noticed that the swap partition entry was completely commented out, with a note that the swap partition wasn't where it had been previously (true, other partitions had been removed which affected the numbering).

I tried getting swap to work, but kept getting errors about not being able to use the partition desired.  So I planned to delete the swap partition in gparted, and re-create it.  Since I no longer need the info on the old data partition, I was going to delete that as well.  gparted wouldn't even recognize or display *any* info for /dev/sda (the SSD).  cfdisk gives the following error:

```
Fatal error:  Bad primary partition 4
```

sda4 is the extended partition that has *all* my Linux partitions in it - root, swap, and data.  Everything.

sfdisk gives the following picture:

```

monte@machin-shin:~$ sudo sfdisk -l


Disk /dev/sda: 31130 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0


   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    191-    192-   1536000    7  HPFS/NTFS/exFAT
		end: (c,h,s) expected (191,89,26) found (1023,254,63)
/dev/sda2        191+  16800-  16610- 133411840    7  HPFS/NTFS/exFAT
/dev/sda3      28859+  31130-   2272-  18244608    7  HPFS/NTFS/exFAT
		start: (c,h,s) expected (1023,254,63) found (1023,134,12)
/dev/sda4      16800+  28859-  12060-  96865280+   5  Extended
		start: (c,h,s) expected (1023,254,63) found (1023,90,59)
/dev/sda5      16800+  20044-   3244-  26056704   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,123,28)
/dev/sda6      20554+  28859-   8305-  66709504   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,147,10)


Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0


   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+   5100-   5101-  40968192   8e  Linux LVM
/dev/sdb2      12449+  60801-  48352- 388385534   83  Linux
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
monte@machin-shin:~$ 

```

So at this point it looks like nearly every partition on that disk is messed up... and specifically the extended partition.

---

### Post by oldfred on 2013-03-24
I do not see overlap. 

What does this say as it is down to sectors not cylinders (which are not used anymore)

sudo fdisk -lu

---

### Post by memilanuk on 2013-03-24
```
monte@machin-shin:~$ sudo fdisk -lu[sudo] password for monte: 


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf80edfa0


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000    7  HPFS/NTFS/exFAT
/dev/sda2         3074048   269897727   133411840    7  HPFS/NTFS/exFAT
/dev/sda3       463628288   500117503    18244608    7  HPFS/NTFS/exFAT
/dev/sda4       269897728   463628288    96865280+   5  Extended
/dev/sda5       269899776   322013183    26056704   83  Linux
/dev/sda6       330209280   463628287    66709504   83  Linux


Partition table entries are not in disk order


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x14a19a9e


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    81938431    40968192   8e  Linux LVM
/dev/sdb2       200002048   976773115   388385534   83  Linux
monte@machin-shin:~$ 



```

---

### Post by oldfred on 2013-03-24
I know it is recommended to have some gap between partitions. The only thing I possibly see is that sda4, the extended ends on the same sector as the sda3 starts. Not 100% sure that is an issue, but if it is complaining then that may be it.

You could make sda6 & the extended a sector or two smaller. If gparted will not open it you may have to export with sfdisk, edit test file and reimport.
 GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

First backup partition table.
sudo sfdisk -d /dev/sda > parts_sda.txt

      Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

---

### Post by memilanuk on 2013-03-24
Looking thru things... by my math, the end of the extended partition sda4, @ 423628288, overlaps the start of sda3 @ 423628289... which I guess is what is giving the system grief.

So... looking at that other article I dumped the partition table to a text file, and I'm currently just using it for a scratch pad to check numbers - I'll dump it again for a fresh copy to back up, and then another to edit when I get to that point.

```

/dev/sda1 : start=     2048, size=  3072000, Id= 7, bootable    3074048
/dev/sda2 : start=  3074048, size=266823680, Id= 7              269897728
/dev/sda4 : start=269897728, size=193730561, Id= 5              463628289
/dev/sda5 : start=269899776, size= 52113408, Id=83              322013184
/dev/sda6 : start=330209280, size=133419008, Id=83              463628288
/dev/sda3 : start=463628288, size= 36489216, Id= 7              499871504

```

I'm thinking that since sda6 is a partition that I want to delete any way, it *hopefully* shouldn't b0rk things too much if I adust the end of that partition and then move the end of the parent extended partition sda4 so it doesn't overlap the start of sda3.

Does that sound about right?

---

### Post by dcstar on 2013-03-27
> **oldfred said:**
> There is disagreement on swap. I find with 4GB of RAM I never use it, so the whole issue is moot. But I have swap on my rotating drive and my installs find it. Someone said having some swap is good for a slightly faster boot. Booting looks for swap and has to time out or not find it, so if it finds it, it may boot very slightly faster.
.........
Discussion of swap on SSD - best not to)
[http://ubuntuforums.org/showthread.php?t=1937251](http://ubuntuforums.org/showthread.php?t=1937251)
.............

It says no such thing, SSD support for Swap is built into the kernel and modern SSD devices should be able to deal with the load.

Overuse of Swap is a generic problem of insufficient RAM for the memory load you are putting on the system, a SSD will actually mitigate it because of the superior IO rate in comparison to rotational drives.

---

