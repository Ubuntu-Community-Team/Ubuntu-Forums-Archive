---
title: "Checking for duplicate files"
date: 2018-09-11
forum: General Help
---

### Post by gumbo64 on 2018-09-11
I am on an Ubuntu 16.04 box.

As a result of a hard disk failure I recovered about 80Gb of pictures and video files with Photorec. Fortunately, most of these files were backed up on another drive, but not all of them.

On the backup drive the files are neatly archived in folders and subfolders, while on the target drive where photorec saved the recovered files the directory structure is obviously gone, and also the file names are apparently different.

So I am looking for an application, possibly with a GUI, to compare the two hard drives so I can delete all the duplicates, indipendently of the directory structure and name of the file.
In other words, I am looking for an app capable of comparing the content of the WHOLE backup drive recursively (not folder by folder) to the recovery drive (also recursively since photorec creates his own recovery folders).

Any suggestion in that regard would be welcome.

---

### Post by HermanAB on 2018-09-11
Hmm... You could write a little Bash script to calculate checksums of all files - make a list of sums and file paths and sort it.

Something based on the 'find exec' and 'md5sum' functions will work.

---

### Post by 1clue on 2018-09-11
From google "linux find duplicate files by content," this was the first hit.

[https://unix.stackexchange.com/questions/71176/find-duplicate-files](https://unix.stackexchange.com/questions/71176/find-duplicate-files)

---

### Post by #&amp;thj^% on 2018-09-11
> **1clue said:**
> From google "linux find duplicate files by content," this was the first hit.

[https://unix.stackexchange.com/questions/71176/find-duplicate-files](https://unix.stackexchange.com/questions/71176/find-duplicate-files)

+1
As much as I like to use the terminal>>> for this "task" I like "fslint-gui" which comes with "fslint".
```
DESCRIPTION
       fslint  is a toolset to find various problems with filesystems, includ&#8208;
       ing duplicate files and problematic filenames etc.

       Individual command line tools are available in addition to the GUI  and
       to   access   them,   one   can   change   to,  or  add  to  $PATH  the
       /usr/share/fslint/fslint directory on  a  standard  install.   Each  of
       these  commands  in  that  directory have a --help option which further
       details its parameters.

       findup - find DUPlicate files

       findnl - find Name Lint (problems with filenames)

       findu8 - find filenames with invalid utf8 encoding

       findbl - find Bad Links (various problems with symlinks)

       findsn - find Same Name (problems with clashing names)

       finded - find Empty Directories

       findid - find files with dead user IDs

       findns - find Non Stripped executables

       findrs - find Redundant Whitespace in files

       findtf - find Temporary Files

       findul - find possibly Unused Libraries

       zipdir - Reclaim wasted space in ext2 directory entries

```
My use:
```
fslint-gui

```

See Screenshot

---

### Post by gumbo64 on 2018-09-11
Recovering the partition table would certainly be the best way to go. The problem happened after moving the partition with Gparted. It successfully completed the task but apparently failed to rewrite the partition table at the end.
On boot the system complains about a bad superblock on the drive, and an error on sector #0, which (to my understanding) is where the partition is supposed to be. Not sure if this can help diagnose the problem.
I have tried recovering the partition table with Testdisk, but after scanning the disk ok, it fails to write it.
The drive is visible in Gparted (unallocated space) but not on gnome-disks
Any alternative to testdisk to recover the partition table ?
A friend suggested EASEUS partition recovery, but it is payware and I am not on Windows :(

---

### Post by oldfred on 2018-09-11
Parted/gparted has a rescue mode. Often easier to use than testdisk. But if testdisk does not find partition(s), parted rescue may not see them either.
       Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue) 
    
Is drive older MBR or newer gpt partitioning? One advantage of gpt is that it has a backup partition table at end of drive and primary partition table can be recovered.
sudo parted -l

---

### Post by gumbo64 on 2018-09-11
Testdisk finds the partition and recognize it as linux. It also finds a backup.
I tried restoring both but it fails to write.
Wonder if this could be related to the error on sector #0. If testdisk it is trying to write to the partition table to a damaged sector...
Not sure what partitioning is on the disk. For sure it is an ext partitioning, possibly 3 or 4. The drive is about 10yrs old (most of which were spent on a shelf though).

Will try gparted rescue as soon as I'm done copying the files, which is taking longer than expected.

---

### Post by oldfred on 2018-09-11
If 10 years old, then it will be MBR(msdos) partitioning. The ext4 is the format of a partition on a drive.

And if drive is that old, it very likely could be a drive issue. MBR is first sector of a drive and where partition table is written.

Does drive support Smart Status? If so, you can use Disks and click in upper right corner for Smart Status. It can run lots of tests, but all I know is good/bad.

---

### Post by gumbo64 on 2018-09-11
The drive do support Smart status. It was checked before moving the partition and it passed the test, it had a few bad sectors though. Being a maxtor I am not surprised :(
Currently "Disks" doesn't show the disk. Gparted (and Testdisk/Photorec) can see the drive, although Gparted takes a few minutes to scan the device and reports errors. I do "ignore" and finally the drive is displayed as unallocated space.
As far as the drive being old, sure old it is. But it has seen very little use as it was used just for occasional backups and stored in his tray on a shelf. I have this habit of keeping all my drives in removable trays so I can hook them up only when required, instead of letting them age when not necessary. Perhaps drives do go bad with age independent of the actual use ? That'd be interesting to know.

Edit:
With regards to the data recovery with photorec, it's been a few hours since the last file was recovered, right now its reading sector  423374687 of 586114704, and 10hrs to go...
Any chance that there might still be data in the remaining sectors or I may as well abort the process ? The drive contained 80Gb of data on a 300Gig drive.

---

### Post by oldfred on 2018-09-11
The one time I ran photorec I had to let it run overnight.
With Linux data is written somewhat randomly in the entire partition. Windows tries to write at beginning of partition, then fragments & needs defrag periodically.

With Photorec, it also recovered my deleted files, some partial files that looked like a file. Some files I wrote multiple times were recovered and I had to do a lot of compares to my somewhat too old backup and each copy of the file. And finding which files to compare took effort as it only recovers by file extension. 

In the old days one way to get a totally locked up drive was to freeze it. That shrank metal just enough that drive would start (once). Issue then was lubrication would dry out. I do not think that fix still works.

---

### Post by gumbo64 on 2018-09-12
Ok so I have tried to recover the drive according to the link posted above by oldfred

As expected I can't backup the partition due to issues on sector 0 I mentioned earlier.

```

read: Input/output error

cg@PC:~$ sudo sfdisk -d /dev/sdc > PT.txt
[sudo] password for cg: 
read: Input/output error

sfdisk: read error on /dev/sdc - cannot read sector 0
 /dev/sdc: unrecognized partition table type
No partitions found
```

and 

```
cg@PC:~$ sudo parted /dev/sdc unit s print
Error: /dev/sdc: unrecognised disk label
```

So I guess I have to forget about recovering the partition ?
Do I have to thrash the drive or it can be fixed with a low level format ?

---

### Post by 1clue on 2018-09-12
IMO backing a partition device that way is not a great idea. I think it's better to back up the mounted partition from the mount point.  For example if /dev/sdc1 is mounted at /some/mount/point and your backup device is /mnt/backup then I would use cp or tar or whatever:

sudo cp -rax /some/mount/point /mnt/backup/

---

### Post by oldfred on 2018-09-12
Post this (in code tags), not sure if fixable or not, but should end with 55 aa

sudo dd if=/dev/sdc count=1 | hexdump -C

---

### Post by gumbo64 on 2018-09-12
here it is

```
cg@PC:~$ sudo dd if=/dev/sdc count=1 | hexdump -C 
[sudo] password for cg: 
1+0 records in
1+0 records out
512 bytes (512 B) copied00000000  fa b8 00 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |................|
, 0,0199139 s, 25,7 kB/s
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  22 cd 07 00 00 00 00 00  |........".......|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

just tried again parted (because the first time I tried it could see the the partition) and now instead of "unrecognized disk label" this is the output:
```

cg@PC:~$ sudo parted /dev/sdc unit s print
Model: ATA Maxtor 6V300F0 (scsi)
Disk /dev/sdc: 586114704s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags
```

---

### Post by oldfred on 2018-09-12
It at least looks like a standard partition table, but all zeros where partition info should be. 1BE - 1FD

[https://thestarman.pcministry.com/asm/mbr/PartTables.htm#mbr](https://thestarman.pcministry.com/asm/mbr/PartTables.htm#mbr)
       446 - 509 1BE - 1FD 64 Master Partition Table 

Not sure if any of other data, means anything. If testdisk or parted rescue still will not write into MBR master table, I might try totally zeroing it out.


Make double sure drive is sdc, sometimes flash drive is sda and then every drive moves up a letter.
      
 Zero out MBR and partition table
dd if=/dev/zero of=/dev/sdc bs=512 count=1

Then see if anything works.

---

### Post by gumbo64 on 2018-09-15
I have no clue what happened in the meantime, but I connected the disk to try the low level format as suggested, and it was recognized by disks (as unallocated space) which didn't happen previously  (only Gparted and Testdisk would recognize the drive).
So I tried again testdisk and apparently it managed to recover the partition, this time no write error message and it says I have to reboot to see the changes. Good !
I checked the drive again with disks (it is not a bootable disk) but its still recognized as unallocated space.
So I reboot with disk connected. The system refuse to boot (as usual) and reports errors on the drive, however not errors on sector 0 as before...
So I reboot with disk disconnected, then connect the disk. Still recognized by Disks as unallocated space. Then I run parted and get an error I had never seen before

```

cg@PC:~$ sudo parted /dev/sdd unit s print
[sudo] password for cg: 
Error: Can't have a partition outside the disk!]
```

so I run fdisk and the disk is recognized (which didn't happen previously) as well as the partitions.

```
cg@PC:~$ sudo fdisk -l
[sudo] password for cg: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ef07e8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   488394751   244196352   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000581ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   308406271   154202112   83  Linux
/dev/sdb2       308408318   312580095     2085889    5  Extended
/dev/sdb5       308408320   312580095     2085888   82  Linux swap / Solaris

[B]Disk /dev/sdd: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cd22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   174674744    87337341   83  Linux
/dev/sdd2       411453440   586115071    87330816   83  Linux[/B]
```

I notice both sda and sdb start at 2048, while sdd starts at 63....
Also total sectors is 586114704, but sdd2 ends at 586115071
Perhaps that is where the problems lies ? Anything I can try to fix this ?

---

### Post by oldfred on 2018-09-15
All drives now start with 2048, 63 was used by XP and Linux until Windows 7. 

Error is that last partition has end beyond end of drive. And you have a large gap between sdd1 & sdd2
I do not know if testdisk or parted rescue will fix that?

It can be fixed with using sfdisk to write a text file & editing text file and restoring it.
But I might try fixparts first also, if testdisk or parted rescue does not work.

       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sdd

---

### Post by gumbo64 on 2018-09-15
Looks like fixparts wants to delete the oversize partition instead of resizing it.

```
sudo fixparts /dev/sdd
[sudo] password for cg: 
FixParts 0.8.8

Loading MBR data from /dev/sdd

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.
Warning: Deleting oversized partition #2! Start = 411453440, length = 174661632

MBR command (? for help):
```

I dont think this is a good idea, so I believe I should quit without saving ? -q

PS.
When the problem happened I was shrinking the linux partition to make room for an NTFS partition, and that was completed successfully and no problem whatsoever, so I had an 80Gb linux partition and the rest unallocated.
Then I moved the linux partition to the end of the drive, and that's when the problem happened.
Perhaps that is the reason of the gap between sdd1 and sdd2 ?
At this point it's hard to tell which one of the two is the actual partition (containing the data). Both are same size.
Wonder how comes there's two partition instead of one anyways..

---

### Post by oldfred on 2018-09-15
If system crashes in the middle of any major partition move, you just about cannot recover. Part of data is in one place and part in another. 
And then only recourse is to restore from your backup. And that is why we always do backups before major system changes.

---

### Post by gumbo64 on 2018-09-16
I had no "system" crash during the partition move. The "move" was "completed successfully", then gparted hanged as it was writing the partition and finally displayed the drive as unallocated space.

What am I supposed to do to manually edit and restore the partition table.
I would like to try this before I let fixparts wipe the oversize partition.

The table below was edited so the end of sdd2 is within the limits of the disk (586114704). Is it OK ?
If not, can you post a copy of the partition table that has some chance to work.```

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   174674744    87337341   83  Linux
/dev/sdd2       411453440   58611**[COLOR=#ff0000]4703[/COLOR]**    87330816   83  Linux

```

---

### Post by oldfred on 2018-09-16
Can you get sfdisk to write the partition table or does error prevent it?
       sudo sfdisk -d /dev/sdc > PT_sdc.txt 

If you can write it, then you can manually edit it to correct ending value & stuff that back into partition table. It should then be seen correctly, but may not have your data. 
If you do not have backups, best to try photorec which is part of testdisk. It takes forever to run, I had to let it run overnight. And you need large drive to copy data to. It only writes files by type not full name, so it took me literately weeks to compare older backup, and all the files it output. I had saved some text files many times & it found every one of them, but not which was newer or older.
      
 [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    
I have gpt, so not sure what newer version of sfdisk outputs. It used to be start & size in sectors. Most tools showed start & end, so you have to do some calculation to get correct size. 

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

Did fixparts show anything useful. It often can convert partitions in memory to correct values & let you then write or quit.

---

### Post by gumbo64 on 2018-09-17
Well, there must be some benevolent entity working on my harddrive overnight :lolflag:!

It seems to improve without me doing nothing ! 
At this point I'm at loss trying to understand what's going on here. Just switched on the computer, inserted the drive to follow your instructions, checked it in disks as usual and now the partition is there ! 
Disk shows one 89Gb ext3 partition (the one containing my data) and 211Gb of unallocated space.
All folders and files magically reappeared.

sfdisk -l still shows the same partition table with the oversize partition ending beyond the disk limits. No changes.

```
Disk /dev/sdd: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cd22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   174674744    87337341   83  Linux
/dev/sdd2       411453440   586115071    87330816   83  Linux
```




Now I am copying all the data to another drive. If I manage to recover all the data should I try fixing the partition or just low level format ?
dd if=/dev/zero of=/dev/sdd bs=512 count=1

EDIT:
All data successfully copied to another drive \\:D/

---

### Post by 1clue on 2018-09-17
I've seen some bizarre behavior on drives before. Back in the 80s is the oddest one, it was in college. A friend of mine had a job programming (I was really jealous) but they had a flaky hard drive. They tried everything. It would start in the morning but then fail after an hour or so. We didn't notice that for quite awhile though. Then somebody took the case off and it was dusty, so they sprayed it with freon. Which, at the time, was what you used to clean off a logic board. Drive started right up, and lasted for a couple hours before failing again. After some experimentation they found that by spraying it again, it would start up and run for awhile. More experimentation and they found that they could keep the drive running by spraying it with freon every so often, without shutting it down. This was in the days of 5.25" hard drives, and they were in the 40 Mb range. You had individual transistors, capacitors and such on the circuit board as well as some integrated circuits.

This being a university campus, there were all sorts of bright minds around, and this was water cooler gossip. Frankly thinking back on this now I can't imagine why they tried so hard to get this working, other than maybe intellectual curiosity. At any time in the past 20 years I would have copied all the data off and thrown it out after the first data error.

At any rate this was in the physics building, and so a few PhD's in physics-related fields got into it. And an Electrical Engineer (also PhD, these were all teachers). Eventually they decided that one or more components was falling out of specifications, about to fail, and was overheating. The freon cooled the part and kept the system going, but when it got hot again those odd errors would start again. To date I've never seen so much research by PhD's devoted to the failure of a single low-cost device. Back then they didn't automatically throw things away, though so that might be part of it. And it had gained a certain amount of momentum as a mysterious error.

---

### Post by gumbo64 on 2018-09-17
Well, lower temps is something I've been thinkin about. These maxtor drives have tendency to overheat and misbehave as a consequence. 
I solved the problem by cutting off the bottom of the tray and adding a second fan into the tray to cool them off, but that was done a while ago and didn't have a problem since. Nonetheless these drive operate at 35-40°C depending on room temp and use of the drive, while other brands in exact same trays seldom operate over room temp.
In the past few days the weather is getting cooler here, perhaps cool weather is my "benevolent entity".

I'm aware this might be offtopic here (or maybe not since after all drives is all we've been discussing).
As far as "hot swapping" SATA drives in trays, some say it's safe to connect/disconnect SATA trays as long as the drive has previously been unmounted.
Others say they should be disconnected only after issuing a command to park the heads.
Others say it should never be connected/disconnected with the computer on because removable SATA trays are not designed to manage the power surge.
What's the real story on the subject ?

---

### Post by 1clue on 2018-09-17
At any rate it seems like you're being reasonable and harvesting every bit of data off that drive you can, when you can.

After that, play with it as much as you like. Overactive curiosity helps you learn, if it doesn't kill you. :)

---

