---
title: "Lost/Corrupt Partition in 12.04 x64 - Help with Recovery"
date: 2016-01-09
forum: General Help
---

### Post by lah-ca on 2016-01-09
Hi,

The BIOS in my daughter's PC got corrupted, and at POST the MOBO reverted to its secondary backup BIOS, resetting the BIOS to basic out of box configuration.

12.04 x64 was installed on the notorious Gigabyte 970A-D3P board, the installation having been a challenge in itself initially.

I believe from my daughter's description that system booted up once with a number of error messages but login could not be done because without IOMMU enabled since neither the USB ports nor the NIC work in Linux with this motherboard.  I think the reset button may have been pushed a number of times, and then all that would come up is a read error message and then a GRUB prompt because the Linux partition with the OS installation could not be read.

The drive cannot be mounted in another Linux system, except for the FAT32 GRUB partition.

If I look at the drive with TestDisk, an EFI GPT partition table is initially auto-detected.  But continuing to Quick Search with this setting, no Linux partitions other than the swap partition are found.  What is found is an MS Data partition.

If I choose an Intel/PC setting initially and proceed to Quick Search, the Linux partition is found and is said to be structurally good.

If I try to look at the drive in GParted, there is a warning message stating that it has GPT signatures, indicating a GPT partition table, but that there is no valid fake msdos partition table ... etc.  The file system is listed as unknown with the flags msftdata.

I am not overly concerned about making the 12.04 installation bootable again, but it would be nice to be able to recover data from the partition for my daughter.

Any suggestions?

I do not have time to post screen shots this evening.  I will add them later.

---

### Post by Bashing-om on 2016-01-10
lah-ca; Hello; My Welcome to the forum.

Be aware that ubuntu is always fixable with a liveDVD(USB), time and effort .
If one wants to retrieve the data from that install, one can also accomplish this mission from a live environment .

Presently, do you have on hand a liveDVD or USB of release 12.04 ?

Once you have the liveDVD we can proceed in whatever direction you choose to pursue .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lah-ca on 2016-01-10
> **Bashing-om said:**
> lah-ca; Hello; My Welcome to the forum.

Be aware that ubuntu is always fixable with a liveDVD(USB), time and effort .
If one wants to retrieve the data from that install, one can also accomplish this mission from a live environment .

Presently, do you have on hand a liveDVD or USB of release 12.04 ?

Once you have the liveDVD we can proceed in whatever direction you choose to pursue .[INDENT][INDENT]it's 'buntu[INDENT][INDENT][INDENT]together we can
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for the welcome and the reply.

I no longer have a liveCD or USB key with 12.04 x64, but this is very easily remedied.

I will not be able to free up the drive for about another 19 hours as I am running PhotoRec on it.  PhotoRec can see and read the partition and is busily doing its near-completely indiscriminate recovery and alpha-numeric-renaming thing.  After years of having ITIL change control beaten into my head, I think it best to do this form of data recovery first as a fall-back recovery point.  Then I can proceed with the potentially more helpful and possibly more dangerous adventures in partition repair.  Despite best efforts on my part to educate my daughter on the virtues of data backup, no backup of her system exists.  There is potential for great pain with the possible loss of photo libraries etc.  PhotoRec offers pain of a different nature - an object lesson in the value of backing things up reinforced by searching tediously through what the app has recovered, looking for things that are important and then renaming and reorganizing them.  

I will prep bootable media with 12.04 and will check back in when PhotoRec has finished running.

Thanks again.

---

### Post by dragonfly41 on 2016-01-11
You might be able to examine (by scripts) the metadata buried in PhotoRec recovered files to filter files into various folders.

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

---

### Post by lah-ca on 2016-01-11
> **dragonfly41 said:**
> You might be able to examine (by scripts) the metadata buried in PhotoRec recovered files to filter files into various folders.

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

Thanks.  The link looks like it will be helpful if I have to go down that route.

There was a minor setback today.  The drive I chose for PhotoRec's recovered files was too small.  I had no idea how much data was on the partition, only the partition size.  Started again with a larger drive.

I will probably be back tomorrow, ready with my 12.04 bootable media.  Fingers crossed.

> **Bashing-om said:**
> lah-ca; Hello; My Welcome to the forum.

Be aware that ubuntu is always fixable with a liveDVD(USB), time and effort .
If one wants to retrieve the data from that install, one can also accomplish this mission from a live environment .

Presently, do you have on hand a liveDVD or USB of release 12.04 ?

Once you have the liveDVD we can proceed in whatever direction you choose to pursue .
[INDENT][INDENT]it's 'buntu[INDENT][INDENT][INDENT]together we can
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks.

Ready if you are.

---

### Post by Bashing-om on 2016-01-12
lah-ca; Great !

So what is the end goal here .. fix the install or pull the data off of it and (RE-)install ?

In any event we want to look at what we are working with.
Boot up the liveDVD to the "try ubuntu" mode to a terminal ( ctl+alt+t at the desktop) .
Post back the outputs - Between Code Tags - of terminal commands:
```

sudo parted -l
sudo parted /dev/sda unit s print
sudo fdisk -lu ## just to see if remnants of a MBR partition scheme is present
sudo blkid -c /dev/null

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Depending on these results, is what we do next . Fix the file system's partition table ?

[INDENT][INDENT]time and effort
[INDENT][INDENT][INDENT]time and effort
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-01-12
Since you mention efi partition and gpt signatures also run this in addition to the suggestions from Bashing-om.
       sudo gdisk -l /dev/sda

If really a gpt partitioned drive gdisk may be able to repair it.
       [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)


 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by lah-ca on 2016-01-12
Hmmm... sorry for the delay here.  

It was hell on earth to get 12.04 installed on the Gygabyte 970A-D3P board in first place, something that I eventually succeeded in doing from a live CD because there was no way I could get the system to boot an x64 version to a USB key.  This probably related to the now well-known issues with the USB ports, NICs and IOMMU and this motherboard.  14.04 will eventually boot off a USB key (boot with an endless list of error messages) if IOMMU is enabled in the BIOS.  14.04 will not boot off a USB key if IOMMU is not enabled.  12.04 will not boot either way.  Must go buy CDs.

But then I just remembered now that the USB 3 ports do work with IOMMU disabled.  I will post this and try again.

---

### Post by oldfred on 2016-01-12
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

      
  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by lah-ca on 2016-01-12
> **Bashing-om said:**
> lah-ca; Great !

So what is the end goal here .. fix the install or pull the data off of it and (RE-)install ?

In any event we want to look at what we are working with.
Boot up the liveDVD to the "try ubuntu" mode to a terminal ( ctl+alt+t at the desktop) .
Post back the outputs - Between Code Tags - of terminal commands:
```

sudo parted -l
sudo parted /dev/sda unit s print
sudo fdisk -lu ## just to see if remnants of a MBR partition scheme is present
sudo blkid -c /dev/null

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Depending on these results, is what we do next . Fix the file system's partition table ?[INDENT][INDENT]time and effort[INDENT][INDENT][INDENT]time and effort
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


OK.  Back from the store with a couple of spindles of media.   If we can make the system bootable, it would be cool as that would greatly ease data recovery (exporting settings from Thunderbird etc) and the restoring of data to new installation of 14.04.  If we can't get the system to boot, just getting the data back with file and folder names would be an excellent second best.

So what do we get when we run your suggested commands?

```

sudo parted -l 

Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  992GB   992GB                         msftdata
 3      992GB   1000GB  8552MB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!  

```


```

sudo parted /dev/sda unit s print 

Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start        End          Size         File system     Name  Flags
 1      2048s        194559s      192512s      fat32                 boot
 2      194560s      1936820223s  1936625664s                        msftdata
 3      1936820224s  1953523711s  16703488s    linux-swap(v1)

```

```

sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      194559       96256    b  W95 FAT32
/dev/sda2          194560  1936820223   968312832   83  Linux
/dev/sda3      1936820224  1953523711     8351744   82  Linux swap / Solaris

```

```

blkid -c /dev/null


/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 12.04.5 LTS amd64" TYPE="iso9660" 
/dev/sda1: UUID="5E72-5DA5" TYPE="vfat" 
/dev/sda3: UUID="a4c9e99e-65a3-48d3-ba25-2530e4c873f2" TYPE="swap" 

```

> **oldfred said:**
> Since you mention efi partition and gpt signatures also run this in addition to the suggestions from Bashing-om.
       sudo gdisk -l /dev/sda

If really a gpt partitioned drive gdisk may be able to repair it.
       [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)


 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Thanks, oldfred.  If memory serves, you have have helped me before, somewhere in the extremely distant past when I had a different user name, maybe back in Dapper days.  

Anyway .... here we go ...

```

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

```

> **oldfred said:**
> Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

      
  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

Thanks again.  

Much more is known about these problematic x64-Linux-unfriendly Gigabyte boards than when I first set the 970A-D3P system up, although I referenced some the links above..  

I have updated the BIOS to the most recent non-Beta version, but there is no relief from the horror.

General rules of thumb for this board.

Set boot to UEFI Only.
Set SATA controllers controllers to ACPI SATA
Enable IOMMU for instalation (don't use the USB 3 ports during installation)
Install
Edit Grub - GRUB_CMDLINE_LINUX="*iommu*=*soft*"
Disablle IOMMU
And life is better

---

### Post by Bashing-om on 2016-01-12
lah-ca; Well ! well ...

Doing my homework ; looks like this may be a good candidate for Ron Smiths FixParts tool .
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

Maybe however 'gdisk' might handle this simpler ?

We now know on this UEFI board there is both MBR and GPT partition tables for the file system. The good news is that 'fdisk' sees the ubuntu partition .
Maybe just a matter of having 'gdisk' rebuild the GPT partition table .

[INDENT][INDENT]study twice
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-01-12
I am surprised that fdisk is showing partitions. It normally just shows one entry that is gpt, so users know drive has partitions and do not overwrite it.

You may have hybrid partitions, which should be avoided.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

You only want the gpt, since you have an ESP - efi system partition and are UEFI booting.
      
 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update gpt primary, gpt backup & protective MBR. Details in rodbooks site on gdisk.

---

### Post by lah-ca on 2016-01-13
Hi,

I am having trouble with the syntax for gdisk.  It is an interactive program of sorts, I think, which must be started with the syntax sudo gdisk /dev/sda with or without the -l flag.  This syntax gets me the output noted above, the option to use MBR, GPT, or blank GPT.  We can go no further without choosing one of the options.

```

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

```

I cannot get gdisk to run with the -b, -p or -v flags, as in gdisk -b /dev/sda2 or /dev/sda.

However, sgdisk, the command line version, is more agreeable.  The command, sudo sgdisk -b /dev/sda2, completed successfully, and I have the resultant backup file saved to USB key. 

This is what sgdisk has to say with the -p and -v flags..

```

sudo sgdisk -p /dev/sda2

Creating new GPT entries.
Disk /dev/sda2: 1936625664 sectors, 923.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9EB7D806-216B-414F-9640-9ADB49BF8AF8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1936625630
Partitions will be aligned on 2048-sector boundaries
Total free space is 1936625597 sectors (923.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

```

```

sudo sgdisk -v /dev/sda2
Creating new GPT entries.

No problems found. 1936625597 free sectors (923.5 GiB) available in 1
segments, the largest of which is 1936625597 (923.5 GiB) in size.

```

No attempt was ever made to create a hybrid partition.  If there is one, it is accidental.  And whatever the problems here may be, they started with a corrupt motherboard BIOS, an automatic reversion to a backup BIOS which was set to defaults (notably: 1. controller set to IDE a state in which 12.04 could not find any drives to partition during initial installation attempts; 2. boot UEFI and Legacy, and 3. IOMMU disabled), multiple attempts to boot the system using the reset button, and finally read error and a grub command prompt,

Ref: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If I look at the disk with Fixparts, I see this:

```

sudo fixparts /dev/sda
FixParts 1.0.1

Loading MBR data from /dev/sda

NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N): 

```

It also just occurred to me that I do not remember how I setup 12.04 initially.  I may have set it up to boot Legacy rather than UEFI.  If I were doing it today, I would choose UEFI because of the improved UEFI compatibility in current distros and because official/semi-official advice, as in AskUbuntu, generally leans towards UEFI installation/boot rather than Legacy, albeit with some reservations.

Hi again.

For interest's sake, here is what TestDisk reveals about the drive and the SDA2 partition.

```

Disk /dev/sda - 1000 GB / 931 GiB - WDC WD1002FAEX-00Y9A0

Please select the partition table type, press Enter when done.
 [Intel  ] Intel/PC partition
>[EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)
 [Humax  ] Humax partition table
 [Mac    ] Apple partition map
 [None   ] Non partitioned media
 [Sun    ] Sun Solaris partition
 [XBox   ] XBox partition
 [Return ] Return to disk selection

```

Note that EFI GPT is auto-selected, I suspect because the partitions GPT signatures have been found.

If we go forward with "Analyse," we get this.

```

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI System                  2048     194559     192512
No FAT, NTFS, ext2, JFS, Reiser, cramfs or XFS marker
 2 P MS Data                   194560 1936820223 1936625664
 2 P MS Data                   194560 1936820223 1936625664
 3 P Linux Swap            1936820224 1953523711   16703488

```

And then if we proceed with "Quick Search," we get this below. 

```

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors

>D MS Data                     2048     194559     192512
Structure: Ok.  
FAT32, 98 MB / 94 MiB


>D MS Data                   194558 1936820221 1936625664
 Structure: Ok.  
EXT4 Large file Sparse superblock Backup superblock, 991 GB / 923 GiB


>P Linux Swap            1936820224 1953523695   16703472
Structure: Ok.  
SWAP2 version 1, 8552 MB / 8155 MiB

```

If for interest's sake we start again and choose "Intel," we get something different.

```

Disk /dev/sda - 1000 GB / 931 GiB - WDC WD1002FAEX-00Y9A0

Please select the partition table type, press Enter when done.
>[Intel  ] Intel/PC partition
 [EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)
 [Humax  ] Humax partition table
 [Mac    ] Apple partition map
 [None   ] Non partitioned media
 [Sun    ] Sun Solaris partition
 [XBox   ] XBox partition
 [Return ] Return to disk selection

```

And then continue with "Analyze" ......

```

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32                    0  32 33    12  28 16     192512
No ext2, JFS, Reiser, cramfs or XFS marker
 2 P Linux                   12  28 17 120561 123 10 1936625664
 2 P Linux                   12  28 17 120561 123 10 1936625664
 3 P Linux Swap           120561 123 11 121601  57 56   16703488

```

And if we proceed to "Quick Search," a very slow search is conducted which produces the following results.

```

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121602 255 63

The harddisk (1000 GB / 931 GiB) seems too small! (< 1490 GB / 1387 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                60079 227 53 180629  67 46 1936625664
   Linux                60082  47 62 180631 142 55 1936625664
   Linux                60083 118  4 180632 212 60 1936625664
   Linux                60085 160 44 180635   0 37 1936625664
   Linux                60089   1  1 180638  95 57 1936625664
   Linux                60089  18 26 180638 113 19 1936625664
   Linux                60337 136 24 181155 162 63 1940942848

EXT4 Large file Sparse superblock Recover, 991 GB / 923 GiB

```

---

### Post by oldfred on 2016-01-13
With gdisk you just load the partition and then go into experts mode. Best to review RodBooks site to understand it.
I hope you did not write a totally new gpt partitioned drive. That may have erased partitions.
       [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
    
First type the ? to see commands:
 sudo gdisk /dev/sda
Command (? for help):

---

### Post by Bashing-om on 2016-01-13
lah-ca; Hello;

See oldfred's last ... Still doing homework on this ..
Trying to talk myself out of option #1
> 
sudo gdisk -l /dev/sda
Found valid MBR and GPT. Which do you want to use?
2 - GPT

Dot my 'i's and cross all 't's before I commit . 
I do not have any GPT partitioned drives and as I have no need of the tool, not installed and as such no experience with it .
We can benefit from other's detailed experience. <- just alook'n around.

We do know we want the partitioning to be GPT without destroying the data .

[INDENT][INDENT]study twice, act once
[/INDENT][/INDENT]

---

### Post by lah-ca on 2016-01-13
Hi oldfred and Bashing-om,

I have been looking around.  It seems the problem, or rather the ***symptom***, here is not uncommon with disks that have been used for Windows previously or have been used in a dual boot situation with Windows and LInux.  The general solution for this ***symptom*** is to have gdisk remove the GPT signatures.  The disk in my daughter's system, however, has never been near Windows of any version, and so while the ***symptom*** may appear to be the same/similar, the root cause is very likely to be different as is the solution, if a solution is possible.  Removing the GPT signatures seems very risky at this point.

I need to scrounge up another hard drive of suitable size so that I can copy the original drive with dd, repeatedly if/as needed, and then have the freedom trial and error experimentation on the copy.

There were initially four possible outcomes for this situation:
1. a bootable repaired system
2. a repaired partition for ease of orderly data recovery
3. a mass unsorted  recovery of renamed files - already done with PhotoRec - lots of pictures were recovered, and pictures were my daughter's primary concern
4. total data loss - not possible now

In this list, we are now up to number 3, which is a lot better than number 4.   In this movement from 4 to 3, life has moved from horror and despair to being highly interesting, if somewhat frustrating.

---

### Post by oldfred on 2016-01-13
You originally showed a UEFI boot system with the FAT32 ESP - efi system partition which would only be on a gpt partitioned drive.

You then only want gpt partitioning with UEFI boot.
While you may be able to convert the gpt to MBR, and reinstall grub in BIOS boot mode, that is a lot of changes. And may lead to lots of issues. 

You do have good backups?

---

### Post by lah-ca on 2016-01-14
Hi oldfred,

> **oldfred said:**
> You originally showed a UEFI boot system with the FAT32 ESP - efi system partition which would only be on a gpt partitioned drive.

You then only want gpt partitioning with UEFI boot.


Yes.  I suspect that this is how I set the system up initially, although it is so long ago now and there were so many different things tried before I got a working installation of 12.04 that I do not remember clearly now.

> **oldfred said:**
> 
While you may be able to convert the gpt to MBR, and reinstall grub in  BIOS boot mode, that is a lot of changes. And may lead to lots of  issues. 


At present, I do not want to convert the gpt to MBR.  I am going to my local FreeGeek (Vancouver), BC, Canada) this morning to see if I can buy a recycled 1TB (or slightly larger) SATA drive.  I will then use dd to copy the original drive.  We can then do whatever to the copy SDA2 partition, however experimental the doing may be, and if the doing is destructive, I can just re-copy the original again.

I am not overly concerned about making the 12.04 installation bootable again.  Bootable is only a desirable best case outcome.  It is not a necessity.

The necessity of data recovery is covered, although in a highly inconvenient manner.

I would be extremely happy with a second best outcome, a readable partition from which data can be recovered in an orderly fashion.

> **oldfred said:**
> 
You do have good backups?

Me?  Personally, yes.  I keep almost nothing on any of my computers, at least nothing that I care about.  I have a server for data storage, and it is backed up daily.  My non-techie wife's computer is backed up for full system recovery, and the backups have been tested with simulated disaster fire drills.

But unfortunately,  the computer here is my daughter's.  She lives about a 45 minute drive away.  She has no backup, despite my suggestions that she back her data up to an external drive on a regular basis.  Although I hate to say it about my own dear daughter, what we have here in this situation is a self-inflicted gunshot wound.  The initial hardware failure (a corrupt BIOS) is not a PICNIC (problem in chair not in computer) situation, but the data recovery situation is.  I have to have sympathy for her as she is my much loved daughter.  You do not need to share this sympathy.  ;)

---

### Post by Bashing-om on 2016-01-14
lah-ca; :)

Just to let yall know I am keeping up.

I still have in mind when you are ready that we sic 'gdisk' on that hard drive.



I did install 'gdisk' and do find the documentatio:
```

man gdisk

```
pretty good in and of it's self.

[INDENT][INDENT]we whoop this sucker yet
[/INDENT][/INDENT]

---

### Post by lah-ca on 2016-01-14
Hi Bash-on and oldfred,

I had to buy a new 1Tb hard drive as 640 Gb was the largest drive FreeGeek had this morning.  

Interestingly dd will not copy the source drive to the new target disk using the command:

```

sudo dd if=/dev/sdx of=/dev/sdy bs=8M && sync

```

The command was copied from here: [http://askubuntu.com/questions/186131/how-do-i-use-dd-to-clone-an-external-usb-drive-installation-to-a-local-hard-disk](http://askubuntu.com/questions/186131/how-do-i-use-dd-to-clone-an-external-usb-drive-installation-to-a-local-hard-disk)

dd would fail 50 Gb into the copy job with a read error from the source disk.  The 50 Gb mark would put the copy progess well into the problematic sda2 partition.

I am working with CloneZilla now.  Interestingly there seem to be options to try to fix errors in Linux partitions on the target drive after the copying.  I did not flag these on this go, but I did force recovery mode sector copying.  

I also have an Easus disk copy boot disk around somewhere, which I understand will do Linux disks.  It is not FOSS like CloneZilla, though.  I also have a licensed copy of the Terabyte disk clone boot disk for Linux around somewhere as well.  We shall see.

CloneZilla seems to be quite fast.  I have never used it before.

---

### Post by Bashing-om on 2016-01-14
lah-ca; Well

```

sudo dd if=/dev/sdx of=/dev/sdy bs=8M && sync

```
Is good where the sd(x) is say sda and the sd(y) is say sdb.
as identified by :
```

sudo parted -l

```
or similar.

However, I have no knowledge of why when the targets are correct that 'dd' would fail to copy .

[INDENT][INDENT]if I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lah-ca on 2016-01-14
> **Bashing-om said:**
> lah-ca; Well

```

sudo dd if=/dev/sdx of=/dev/sdy bs=8M && sync

```
Is good where the sd(x) is say sda and the sd(y) is say sdb.
as identified by :
```

sudo parted -l

```


Yes.  I copied the syntax but changed the disks to sdb (source) and sda (target), designations verified in gparted before hitting the enter key to lauch the dd command.

---

### Post by oldfred on 2016-01-15
I believe dd fails on file corruption. ddrescue may then work.

 Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://ubuntuforums.org/showthread.php?t=2305215&p=13401824#post13401824](http://ubuntuforums.org/showthread.php?t=2305215&p=13401824#post13401824)

---

### Post by lah-ca on 2016-01-15
Hi Bash-on and oldfred,

It took CloneZilla about 5 or 6 hours to copy the 1 Tb drive, sector by sector.  Now I have a copy to experiment, with and if things don't work out, I can make another copy.

What would we like to try first?

---

### Post by oldfred on 2016-01-15
I still suggest gdisk.

       sudo gdisk /dev/sda
Command (? for help): 

Then use ? to see commands and see if just a w writes corrected partition table.

Then you may need a fsck on the partition(s).
      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Bashing-om on 2016-01-15
lah-ca; Well ...

My thoughts are to try 'gdisk' see what it can see and correct.
To that end :
```

sudo gdisk -l /dev/sdc
sudo gdisk -i /dev/sdc
sudo gdisk -v /dev/sdc

```
Where 'sd(c)' is the clonezilla copy identifier for that hard drive. - change as required from 'sdc' as verified by other tools.
As we  "look" at the the hard drive partitioning. No changes will be made here .. until we (w)rite the changes in memory back to the hard drive.

I do expect the -v option to reveal the more relevant info .
My reference is the man page for 'gdisk' :
```

man gdisk

```

Depending on what the utility reports is what we do next. Now that the grunt work is done ->
[INDENT][INDENT][INDENT]the fun part begins
[/INDENT][/INDENT][/INDENT]

---

### Post by lah-ca on 2016-01-15
> **oldfred said:**
> I still suggest gdisk.

       sudo gdisk /dev/sda
Command (? for help): 

Then use ? to see commands and see if just a w writes corrected partition table.

Then you may need a fsck on the partition(s).
      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Hi oldfred,

OK, so I used gdisk w after choosing GPT on the first screen.

Then I ran:[INDENT]sudo e2fsck -C0 -p -f -v /dev/sda2
[/INDENT]

Which produced this:[INDENT]e2fsck: Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
[/INDENT]

Normally I would have stopped at this point, but since we are on adventure here and since there is a safety net, I ran:[INDENT]sudo e2fsck -f -y -v /dev/sda2
[/INDENT]

This command produced a near-endless series of error/auto-correction messages before it finished running.

Trying to mount the volume produced this message:[INDENT]Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/INDENT]

dmesg revealled this:[INDENT][ 1925.213357] EXT4-fs (sda2): ext4_check_descriptors: Checksum for group 0 failed (3636!=0)
[ 1925.213365] EXT4-fs (sda2): group descriptors corrupted!

[/INDENT]

Back to CloneZilla.

[https://youtu.be/yubso_i0ZCI](https://youtu.be/yubso_i0ZCI)

;)

> **Bashing-om said:**
> lah-ca; Well ...

My thoughts are to try 'gdisk' see what it can see and correct.
To that end :
```

sudo gdisk -l /dev/sdc
sudo gdisk -i /dev/sdc
sudo gdisk -v /dev/sdc

```
Where 'sd(c)' is the clonezilla copy identifier for that hard drive. - change as required from 'sdc' as verified by other tools.
As we  "look" at the the hard drive partitioning. No changes will be made here .. until we (w)rite the changes in memory back to the hard drive.

I do expect the -v option to reveal the more relevant info .
My reference is the man page for 'gdisk' :
```

man gdisk

```

Depending on what the utility reports is what we do next. Now that the grunt work is done ->[INDENT][INDENT][INDENT]the fun part begins
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing-om,

We will try this on the next go round after CloneZilla is done.

Hi oldfred and Bashing-om,

It seems that the Clonezilla process is not nuetral.  Now when I use gdisk, I get a different response than previously when looking at the source disk.

```

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 

```

I am going to shut down and re-examine the source disk.

Hmmm..... most interesting ....

The original source disk reads quite differently.

```

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 

```

I think I will try my Easus disk copy disk, if I can find it, and see what the results are.

BTW, oldfred and Bashin-om, you guys are being incredibly helpful, above and beyond as it were.  Any time you want to suggest pulling the plug on life support here, go ahead.  I have already greatly imposed upon your time and good natures.   Thanks.

---

### Post by Bashing-om on 2016-01-16
lah-ca; welp ....

as to:
> 
BTW, oldfred and Bashin-om, you guys are being incredibly helpful, above and beyond as it were. Any time you want to suggest pulling the plug on life support here, go ahead. I have already greatly imposed upon your time and good natures. Thanks.

We are here to help, guide and assist ... and in my case what I can further learn. There is no quit in our natures so long as you are working .

Be aware that the w option in 'gdisk' will write out what the partition is in memory back to the hard drive . We want that image in memory to be correct before the write operation. We want that image to be GPT .

[INDENT][INDENT]careful is no accident
[/INDENT][/INDENT]

---

### Post by LostFarmer on 2016-01-16
[QUOTECaution: invalid backup GPT header, but valid main header; regenerating backup header from main header.][/QUOTE]The backup GPT header is located at the very last sector of disk.  When you made the copy of hdd, the new one was bigger , there for the last sectors are not the data as original disk.

---

### Post by lah-ca on 2016-01-16
> **LostFarmer said:**
>  Caution: invalid backup GPT header, but valid main header; regenerating backup header from main header.  The backup GPT header is located at the very last sector of disk.  When you made the copy of hdd, the new one was bigger , there for the last sectors are not the data as original disk.

Thanks.  I understand what you are saying, but I don't think this is the case here.  

The two drives are both Western Digital 1 Tb drives and are read by the OS and being indentical in size.  There is something in the way that CloneZilla copied the drive that produced this strange result.  

The Easus disk copy utility, also Linux-based, has produced a clone that seems to read the same as the source disk, that is it is not showing any weirdness that was not already associated with the source disk.

> **Bashing-om said:**
> lah-ca; Well ...

My thoughts are to try 'gdisk' see what it can see and correct.
To that end :
```

sudo gdisk -l /dev/sdc
sudo gdisk -i /dev/sdc
sudo gdisk -v /dev/sdc

```
Where 'sd(c)' is the clonezilla copy identifier for that hard drive. - change as required from 'sdc' as verified by other tools.
As we  "look" at the the hard drive partitioning. No changes will be made here .. until we (w)rite the changes in memory back to the hard drive.

I do expect the -v option to reveal the more relevant info .
My reference is the man page for 'gdisk' :
```

man gdisk

```

Depending on what the utility reports is what we do next. Now that the grunt work is done ->[INDENT][INDENT][INDENT]the fun part begins
[/INDENT]
[/INDENT]
[/INDENT]


OK.  Easus seems to have produced a clone which reads the same as the source.

I cannot run gdisk with either the -I or -v flags.  These are reported as invalid syntax.  The ***i*** and ***v*** are options in a secondary interactive menu brought up by pressing ***?*** .

So first:

```

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 2
Using GPT and creating fresh protective MBR.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): EC20BE89-5459-4B82-9A32-B7E7C220A698
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          194559   94.0 MiB    EF00  
   2          194560      1936820223   923.5 GiB   0700  
   3      1936820224      1953523711   8.0 GiB     8200  

```

Next*** i*** :

```

Command (? for help): i
Partition number (1-3): 2
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 8E2B4C8A-24E8-4E8B-9A29-170F21D47EB6
First sector: 194560 (at 95.0 MiB)
Last sector: 1936820223 (at 923.5 GiB)
Partition size: 1936625664 sectors (923.5 GiB)
Attribute flags: 0000000000000000
Partition name: ''

```

Next ***v*** :

```

Command (? for help): v

No problems found. 3437 free sectors (1.7 MiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

```

---

### Post by Bashing-om on 2016-01-16
lah-ca; Hey


Well that looks like progress ... However, for the file type "code" I had expected it to be 8300 rather than 0700. I have to do homework and find out what that means and if we should or have a means to change that "code'
```

Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          194559   94.0 MiB    EF00  
   2          194560      1936820223   923.5 GiB   0700  
   3      1936820224      1953523711   8.0 GiB     8200

```
Before we (w)rite the changes to hard drive.

Homework: from:
[http://www.rodsbooks.com/linux-fs-code/](http://www.rodsbooks.com/linux-fs-code/)
says:
> 
with a Linux filesystem (Spare /boot) that has a 0x0700 type code—GPT fdisk's way of identifying a Microsoft Basic Data partition. (Since GPT fdisk doesn't scan partitions' contents to identify the filesystem, you'll have to know enough about your disk to know which partitions are actually Linux filesystem partitions.)
 bk
To change the type code of the Linux partition, use the t command to set a code of 0x8300 (GPT fdisk's internal code for the Linux Filesystem Data type):

Command (? for help): t
Partition number (1-3): 2
Current type is 'Microsoft basic data'
Hex code or GUID (L to show codes, Enter = 8300): 8300
Changed type of partition to 'Linux filesystem'


so yeah we can.

[INDENT][INDENT][INDENT]I think we should
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-01-16
Rod Smith did not think it was correct to have just one type. So 8300 was created for Linux partitions, otherwise they were just Microsoft. So depending on how old partitioning is, may be what type it is. Not critical but you can change to Linux type for Linux partitions.

 New code for NTFS gpt partition
[http://ubuntuforums.org/showthread.php?t=1822452](http://ubuntuforums.org/showthread.php?t=1822452)
Change type code  to 8300 with dual booting with Windows on gpt
[http://www.rodsbooks.com/linux-fs-code/index.html](http://www.rodsbooks.com/linux-fs-code/index.html)
sudo gdisk /dev/sdd
Command (? for help): t
Partition number (1-3): 2
Current type is 'Microsoft basic data'
Hex code or GUID (L to show codes, Enter = 8300): 8300
Changed type of partition to 'Linux filesystem'
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by LostFarmer on 2016-01-16
From your post #16

```
 >D MS Data                   194558 1936820221 1936625664  Structure: Ok.   EXT4 Large file Sparse superblock Backup superblock, 991 GB / 923 GiB
```  with the start  2 sectors before what is listed in the partition table, it says it has a good structure.  I would re-run 'testdisk' and select only that partition to be written to the partition table. with luck. The output does show the fat32 partition would overlap by 2 sectors so both could not be written to disk.

---

### Post by Bashing-om on 2016-01-19
lah-ca; Hey, hey ....

How is your situation progressing ?
I can now fully commiserate with you.

I also had a similar situation that I have managed to recover from. Somehow I managed to trash my partition tables on 2 hard drives !
Took me a while to be able to boot into a working system - could not even boot up a liveDVD - and even longer to determine the fault was the partition tables . e2fsck to my rescue, repair to my main drive and  and sparring of the superblock on my backup drive; All is well again in my world.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lah-ca on 2016-01-19
Hi all,

I have been sick in bed with the flu for the last couple of days.

I tried proceeding in the opposite direction we have been going.  We have been assuming that the partition was initially EFI/GPT.  I tried removing the GPT signatures from the partition on the clone drive to see what the results were.  The results were not pretty.

My daughter extends her thanks to all who have been offering help here.  But she wants her computer back.  She is content to wade through the recovered masses of JPEG and ODT files, which at this point are the only things she really cares about.  The music and video libraries she can rebuild.  Email is not a concern.  She has asked me just to reload the system.

The experience here has been very educational.  I am sorry that I cannot persist with the recovery efforts to a more satisfactory conclusion.

Now I will probably subject the drive to Western Digital's data destructive utilities to wipe and test it.  Then I will reload with 14.04, copy the recovered data, and then script mass deletions of file types that are not of interest.

Thank you, Bashing-om, oldfred, and LostFarmer.  You guys have been great.

My daughter is going to do backups.

---

### Post by Bashing-om on 2016-01-19
lah-ca; Ho Kay ....

We understand that time is of an essence and there is a point of diminishing return of effort.

When you have applied that nuclear solution,
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by lah-ca on 2016-01-29
Thanks again to all.  I note that I forgot to thank Dragonfly41 above, so I will do it now.  Thanks.

Because of a lack of time (not because of a lack of interest), I have applied a thermonuclear solution to the problem.

Quick review in point form:
 
[LIST]
[*]Gigabyte 970A-D3P - a notoriously Linux-unfriendly MOBO - installation probably best in UEFI only mode, controller set to AHCPI/SATA for 12.04 installation media to be able to see and partition hard drive - IOMMU  enabled for NIC and USB ports to function during installation (IOMMU can later be disabled if GRUB is set to iommu=soft) 
[*](970A-D3P, not a bad MOBO, per se, just not a nice one for Linux - ref: [http://www.gigabyte.com/products/product-page.aspx?pid=4642#ov](http://www.gigabyte.com/products/product-page.aspx?pid=4642#ov) ) 
[*]BIOS spontaneously corrupted and system reset, loading backup BIOS with default settings. 
[*]System reset button was probably pushed many times. 
[*]Eventually GRUB could not read the data partition. 
[*][COLOR=#ff0000]***NEW INFO***[/COLOR] - a techie friend of daughter's boyfriend may have used some boot-repair utility on the system - boyfriend does not know enough to explain more thoroughly - friend of boyfriend is evasive. 
[*]Partition could not be mounted - unknown file system. 
[*]Rough/raw recovery of files was done with PhotoRec - ref: [http://www.cgsecurity.org/](http://www.cgsecurity.org/) (I believe Testdisk is in the repository and it includes Photorec). 
[*]Disk/partition was examined with Testdisk (a nice utility BTW). 
[*]Disk/partition was examined with gdisk - ref: [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/) (also a very nice utility- Thx, oldfred) 
[*]Disk/partion was examined with FixParts - ref: [http://www.rodsbooks.com/fixparts/index.html](http://www.rodsbooks.com/fixparts/index.html) (also a nice utility) 
[*]The results of the examinations were ambiguous showing some indications of the partion being  hybrid. 
[*]Disk could not be cloned with dd for safety backup - dd failed with read errors 
[*]Disk was cloned with Clonezilla but the copy appeared to be different from the source with regards to partition problems - ref: [http://clonezilla.org/](http://clonezilla.org/) . 
[*]Disk was cloned with Easus Disk Copy, a (home-use) freeware, Linux-based, ***but not FOSS***, utility - ref: [http://www.easeus.com/disk-copy/index.htm](http://www.easeus.com/disk-copy/index.htm) 
[*]Various attempts were made to repair partition (on cloned disk) - details in thread above. 
[*]Time ran out. 
[*]Tested and wiped original disk with Western Digital's LifeGuard utilities - no longer available in a bootable ISO format, except as part of Hiren's Boot CD - ref: [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd) 
[*]Updated BIOS on MOBO to version F6f - ref: [http://www.gigabyte.com/products/product-page.aspx?pid=4642#bios](http://www.gigabyte.com/products/product-page.aspx?pid=4642#bios) 
[*]Installed 14.04 
[*]Copied data recovered by PhotoRec (approx 184 Gb in some 174,000 files in 1,400+ folders with about 500 files per folder) to reloaded system. 
[*]Scripted mass deletion of files of no interest, by type and/or size. 
[*]Scripted mass deletion of empty folders. 
[*]Data reduced to about 80 Gb in some 300+ folders, which my daughter can wade through. 
[*]Documented system setup for daughter and walked her through BIOS settings - she is quite techie although she denies it - a hardcore Ubuntu user since Dapper. 
[*]System is home. 
[/LIST]

Thanks again.

---

### Post by Bashing-om on 2016-01-29
lah-ca; Uh Huh !

A lot of time, work, and effort  ...... We do appreciate the details on your procedure.

[INDENT][INDENT]just goes to show
[INDENT][INDENT][INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

