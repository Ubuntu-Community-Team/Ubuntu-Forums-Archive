---
title: "Unable to mount NTFS drives"
date: 2017-12-07
forum: General Help
---

### Post by thanekrios on 2017-12-07
Hello guys, this is probably a question that has been asked quite a bit. I am **unable to mount my NTFS drives** (This includes the ones I use with Windows to store stuff, not only the one that has Windows installed on it, but only the NTFS ones) because of this issue:

```
Error mounting /dev/sdb1 at /media/v/Storage: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/v/Storage"' exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0x0000ffff  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0000ffff  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0000ffff  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0000ffff  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0000ffff  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0000ffff  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0000ffff  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x0000ffff  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x88a2c6d9  size: 1024   usa_ofs: 21033  usa_count: 57537: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x57a5895b  size: 1024   usa_ofs: 7400  usa_count: 9087: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xecbaa0af  size: 1024   usa_ofs: 46228  usa_count: 10133: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xe9eab6f3  size: 1024   usa_ofs: 478  usa_count: 14661: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xb5e712b7  size: 1024   usa_ofs: 49758  usa_count: 8896: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x2c095a55  size: 1024   usa_ofs: 60088  usa_count: 55058: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x3da50e5f  size: 1024   usa_ofs: 24279  usa_count: 36341: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x7d5b6928  size: 1024   usa_ofs: 40154  usa_count: 37321: Invalid argument
$MFTMirr error: Invalid mft record for 'mft record'.
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

I **do not have a RAID setup, and fast boot is disabled**, so I do not know what the problem could be, maybe you can?

I appreciate any help you can provide. Thank you.-

---

### Post by dragonfly41 on 2017-12-08
This is what I do for a NTFS partition shared between Windows and Ubuntu in dual boot mode.

Install ntfsfix

Then run .. ```
sudo ntfsfix sdb1
``` .. where sdb1 is your shared NTFS partition.

[COLOR=#b22222][Late apology][/COLOR]
[COLOR=#b22222]
[/COLOR][COLOR=#b22222]That path should have been ... [/COLOR]
[COLOR=#b22222]```
sudo ntfsfix /dev/sdb1
```
[/COLOR][COLOR=#b22222]based on information read in post #1[/COLOR]
[COLOR=#b22222]
[/COLOR][COLOR=#b22222]First run ... [/COLOR]
[COLOR=#b22222]```
ntfsfix --help
```
[/COLOR][COLOR=#b22222]to read instructions.[/COLOR]
[COLOR=#b22222]```
[/COLOR]
[COLOR=#b22222]ntfsfix v2015.3.14AR.1 (libntfs-3g)[/COLOR]

[COLOR=#b22222]Usage: ntfsfix [options] device[/COLOR]
[COLOR=#b22222]    Attempt to fix an NTFS partition.[/COLOR]

[COLOR=#b22222]    -b, --clear-bad-sectors Clear the bad sector list[/COLOR]
[COLOR=#b22222]    -d, --clear-dirty       Clear the volume dirty flag[/COLOR]
[COLOR=#b22222]    -h, --help              Display this help[/COLOR]
[COLOR=#b22222]    -n, --no-action         Do not write anything[/COLOR]
[COLOR=#b22222]    -V, --version           Display version information[/COLOR]

[COLOR=#b22222]For example: ntfsfix /dev/hda6[/COLOR]
[COLOR=#b22222]
```[/COLOR][COLOR=#b22222]
[/COLOR]
[COLOR=#b22222]and second as suggested in post #8 [/COLOR][COLOR=#b22222]run ... [/COLOR]
[COLOR=#b22222]```
sudo fdisk -l
```
[/COLOR][COLOR=#b22222]to check correct partition path to use as argument.[/COLOR]

---

### Post by oldfred on 2017-12-08
Fast boot in UEFI is different than fast start up in Windows.
Are you sure you have fast start up off and any hibernation settings off?
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

And to dragonfly41's suggestion. ntfsfix actually does not do much, but it turns on the  chkdsk needed flag so when you boot into Windows, Windows will run chkdsk which may fix issues.

---

### Post by thanekrios on 2017-12-08
> **dragonfly41 said:**
> This is what I do for a NTFS partition shared between Windows and Ubuntu in dual boot mode.

Install ntfsfix

Then run .. ```
sudo ntfsfix sdb1
``` .. where sdb1 is your shared NTFS partition.

This is what I get from ntfsfix:

```
xx@xx-PC:~$ sudo ntfsfix sda3
[sudo] password for v: 
Failed to determine whether sda3 is mounted: No such file or directory
Mounting volume... Failed to access 'sda3': No such file or directory
Error opening 'sda3': No such file or directory
FAILED
Attempting to correct errors... Failed to access 'sda3': No such file or directory
Error opening 'sda3': No such file or directory
FAILED
Failed to startup volume: No such file or directory
Failed to access 'sda3': No such file or directory
Error opening 'sda3': No such file or directory
Volume is corrupt. You should run chkdsk. 
```

After running chkdsk on Windows, it produces the same output.

> **oldfred said:**
> Fast boot in UEFI is different than fast start up in Windows.
Are you sure you have fast start up off and any hibernation settings off?
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

And to dragonfly41's suggestion. ntfsfix actually does not do much, but it turns on the  chkdsk needed flag so when you boot into Windows, Windows will run chkdsk which may fix issues.

This is what I get:

```
C:\Windows\system32>chkdsk C:
The type of the file system is NTFS.


WARNING!  /F parameter not specified.
Running CHKDSK in read-only mode.


Stage 1: Examining basic file system structure ...
  380416 file records processed.
File verification completed.
  3651 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  786 reparse records processed.
  445440 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.
  786 reparse records processed.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  32513 data files processed.
CHKDSK is verifying Usn Journal...
  35704264 USN bytes processed.
Usn Journal verification completed.


Windows has scanned the file system and found no problems.
No further action is required.


  31457279 KB total disk space.
  22966692 KB in 109671 files.
     85564 KB in 32514 indexes.
         0 KB in bad sectors.
    461223 KB in use by the system.
     42912 KB occupied by the log file.
   7943800 KB available on disk.


      4096 bytes in each allocation unit.
   7864319 total allocation units on disk.
   1985950 allocation units available on disk.


C:\Windows\system32>chkdsk D:
The type of the file system is NTFS.
Volume label is Storage.


WARNING!  /F parameter not specified.
Running CHKDSK in read-only mode.


Stage 1: Examining basic file system structure ...
  47616 file records processed.
File verification completed.
  887 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  116 reparse records processed.
  49176 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.
  116 reparse records processed.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  781 data files processed.
CHKDSK is verifying Usn Journal...
  35998672 USN bytes processed.
Usn Journal verification completed.


Windows has scanned the file system and found no problems.
No further action is required.


 262143999 KB total disk space.
 177463104 KB in 5681 files.
     21568 KB in 782 indexes.
         0 KB in bad sectors.
    156863 KB in use by the system.
     65536 KB occupied by the log file.
  84502464 KB available on disk.


     65536 bytes in each allocation unit.
   4095999 total allocation units on disk.
   1320351 allocation units available on disk.


C:\Windows\system32>chkdsk E:
The type of the file system is NTFS.
Volume label is Software.


WARNING!  /F parameter not specified.
Running CHKDSK in read-only mode.


Stage 1: Examining basic file system structure ...
  22080 file records processed.
File verification completed.
  0 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  37 reparse records processed.
  24116 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.
  37 reparse records processed.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  1019 data files processed.
CHKDSK is verifying Usn Journal...
  23151728 USN bytes processed.
Usn Journal verification completed.


Windows has scanned the file system and found no problems.
No further action is required.


  15724608 KB total disk space.
   3035264 KB in 10292 files.
     22592 KB in 1020 indexes.
         0 KB in bad sectors.
    112960 KB in use by the system.
     65536 KB occupied by the log file.
  12553792 KB available on disk.


     65536 bytes in each allocation unit.
    245697 total allocation units on disk.
    196153 allocation units available on disk.


C:\Windows\system32>chkdsk F:
The type of the file system is NTFS.
Volume label is Large Software.


WARNING!  /F parameter not specified.
Running CHKDSK in read-only mode.


Stage 1: Examining basic file system structure ...
  164736 file records processed.
File verification completed.
  1 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  8 reparse records processed.
  224124 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.
  8 reparse records processed.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  29694 data files processed.


Windows has scanned the file system and found no problems.
No further action is required.

``` 

From what I understand, everything seems ok. After that, running ntfsfix again will produce the same output I posted above.

Also, I'm pretty sure I have Fastboot disabled:

[IMG]https://i.imgur.com/URciu5W.png[/IMG]

And I'm booting in BIOS mode.

This is my partitioning scheme, maybe it can help you (light blue partitions are logical, and blur partitions are primary):

[IMG]https://i.imgur.com/U9OpU0s.png[/IMG]

Thank you for the responses guys.

---

### Post by oldfred on 2017-12-08
Did you change the setting on what power button does. You just showed the power button not the shutdown configuration.
Also please post screenshots as attachments.

 If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 

If you run chkdsk without any parameters, it just runs a report, does not fix anything.
And you may need chkdsk on all NTFS or FAT32 partitions.

---

### Post by Yellow Pasque on 2017-12-08
> After that, running ntfsfix again will produce the same output I posted above.

You are giving an invalid path.

Should be: 
```
sudo ntfsfix /dev/sda3
```
NOT:
```
sudo ntfsfix sda3
```

---

### Post by thanekrios on 2017-12-08
You are quite right. I ran chkdsk /f now. Here is the output:
```

 C:\Windows\system32>chkdsk /f D:The type of the file system is NTFS.
Volume label is Storage.


Stage 1: Examining basic file system structure ...
  47616 file records processed.
File verification completed.
  887 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  116 reparse records processed.
  49176 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.
  116 reparse records processed.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  781 data files processed.
CHKDSK is verifying Usn Journal...
  35999720 USN bytes processed.
Usn Journal verification completed.


Windows has scanned the file system and found no problems.
No further action is required.


 262143999 KB total disk space.
 173039488 KB in 5681 files.
     21568 KB in 782 indexes.
         0 KB in bad sectors.
    156863 KB in use by the system.
     65536 KB occupied by the log file.
  88926080 KB available on disk.


     65536 bytes in each allocation unit.
   4095999 total allocation units on disk.
   1389470 allocation units available on disk.


C:\Windows\system32>chkdsk D: /f
The type of the file system is NTFS.
Volume label is Storage.


Stage 1: Examining basic file system structure ...
  47616 file records processed.
File verification completed.
  887 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  116 reparse records processed.
  49178 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.
  116 reparse records processed.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  782 data files processed.
CHKDSK is verifying Usn Journal...
  35999920 USN bytes processed.
Usn Journal verification completed.


Windows has scanned the file system and found no problems.
No further action is required.


 262143999 KB total disk space.
 173039552 KB in 5682 files.
     21568 KB in 783 indexes.
         0 KB in bad sectors.
    156863 KB in use by the system.
     65536 KB occupied by the log file.
  88926016 KB available on disk.


     65536 bytes in each allocation unit.
   4095999 total allocation units on disk.
   1389469 allocation units available on disk.


C:\Windows\system32>chkdsk E: /f
The type of the file system is NTFS.


Chkdsk cannot run because the volume is in use by another
process.  Chkdsk may run if this volume is dismounted first.
ALL OPENED HANDLES TO THIS VOLUME WOULD THEN BE INVALID.
Would you like to force a dismount on this volume? (Y/N) y
Volume dismounted.  All opened handles to this volume are now invalid.
Volume label is Software.


Stage 1: Examining basic file system structure ...
  22080 file records processed.
File verification completed.
  0 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  37 reparse records processed.
  24116 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.
  37 reparse records processed.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  1019 data files processed.
CHKDSK is verifying Usn Journal...
  23152504 USN bytes processed.
Usn Journal verification completed.


Windows has scanned the file system and found no problems.
No further action is required.


  15724608 KB total disk space.
   3035264 KB in 10292 files.
     22592 KB in 1020 indexes.
         0 KB in bad sectors.
    112960 KB in use by the system.
     65536 KB occupied by the log file.
  12553792 KB available on disk.


     65536 bytes in each allocation unit.
    245697 total allocation units on disk.
    196153 allocation units available on disk.


C:\Windows\system32>chkdsk F: /f
The type of the file system is NTFS.
Volume label is Large Software.


Stage 1: Examining basic file system structure ...
  164736 file records processed.
File verification completed.
  1 large file records processed.
  0 bad file records processed.


Stage 2: Examining file name linkage ...
  8 reparse records processed.
  224124 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered to lost and found.
  8 reparse records processed.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
  29694 data files processed.


Windows has scanned the file system and found no problems.
No further action is required.


 104856191 KB total disk space.
  52536832 KB in 15240 files.
     96128 KB in 29696 indexes.
         0 KB in bad sectors.
    231359 KB in use by the system.
     65536 KB occupied by the log file.
  51991872 KB available on disk.


     65536 bytes in each allocation unit.
   1638377 total allocation units on disk.
    812373 allocation units available on disk.



```

Tried running ntfsfix after this, and the output:
```

xx@xx-PC:~$ sudo ntfsfix sda3
[sudo] password for v: 
Failed to determine whether sda3 is mounted: No such file or directory
Mounting volume... Failed to access 'sda3': No such file or directory
Error opening 'sda3': No such file or directory
FAILED
Attempting to correct errors... Failed to access 'sda3': No such file or directory
Error opening 'sda3': No such file or directory
FAILED
Failed to startup volume: No such file or directory
Failed to access 'sda3': No such file or directory
Error opening 'sda3': No such file or directory
Volume is corrupt. You should run chkdsk.

```

Edit: Corrected the path:

```
xx@xx-PC:~$ sudo ntfsfix /dev/sda3
Mounting volume... Error opening '/dev/sda3': No such device or address
FAILED
Attempting to correct errors... Error opening '/dev/sda3': No such device or address
FAILED
Failed to startup volume: No such device or address
Error opening '/dev/sda3': No such device or address
Volume is corrupt. You should run chkdsk.
```

---

### Post by Yellow Pasque on 2017-12-08
> Mounting volume... Error opening '/dev/sda3': No such device or address

Then you have the wrong partition name. Double check:
```
sudo fdisk -l
```

---

### Post by dragonfly41 on 2017-12-09
Correction with apology added to post #2.

---

### Post by thanekrios on 2017-12-09
Ah I see, I was doing it wrong. My bad. Still no good news:

```
@ ~ $ sudo ntfsfix /dev/sdb2
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
NTFS signature is missing.
Unrecoverable error
Volume is corrupt. You should run chkdsk.
@ ~ $ sudo ntfsfix -b  /dev/sdb2
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
NTFS signature is missing.
Unrecoverable error
Volume is corrupt. You should run chkdsk.
@ ~ $ sudo ntfsfix -d /dev/sdb2
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
NTFS signature is missing.
Unrecoverable error
Volume is corrupt. You should run chkdsk.

```

The is the output of fdisk -l by the way:

```
isk /dev/sda: 223,6 GiB, 240057409536 bytes, 468862128 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6a680bfe


Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048   1126399   1124352  549M  7 HPFS/NTFS/exFAT
/dev/sda2         1126400  64040959  62914560   30G  7 HPFS/NTFS/exFAT
/dev/sda3        64041086 305202869 241161784  115G  f W95 Ext'd (LBA)
/dev/sda4       305203200 345202687  39999488 19,1G 83 Linux
/dev/sda5        64041088  95490359  31449272   15G  7 HPFS/NTFS/exFAT
/dev/sda6        95490423 305202869 209712447  100G  7 HPFS/NTFS/exFAT


Partition table entries are not in disk order.




Disk /dev/sdb: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D832EA20-DC81-03A6-88BA-0C7620B7E900


Device         Start       End   Sectors  Size Type
/dev/sdb1       2048 524290047 524288000  250G Microsoft basic data
/dev/sdb2  524290048 728772607 204482560 97,5G Microsoft basic data
/dev/sdb3  728772608 928772095 199999488 95,4G Linux filesystem
/dev/sdb4  928772096 944773119  16001024  7,6G Linux filesystem
/dev/sdb5  944773120 976771071  31997952 15,3G Linux swap

```

Thank you all for the patience  :D

---

### Post by oldfred on 2017-12-09
Partition boot sector (PBR or BS) has to have NTFS signature. There is a backup of the BS  in NTFS partitions and testdisk can restore that if it is valid.
Some users mistakenly install grub to PBR, so instructions may mention grub, but solution potentially is the same.

       [http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

