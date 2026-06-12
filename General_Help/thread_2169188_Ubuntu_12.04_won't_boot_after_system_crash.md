---
title: "Ubuntu 12.04 won't boot after system crash"
date: 2013-08-20
forum: General Help
---

### Post by russ3 on 2013-08-20
Late the other night, Ubuntu crashed suddenly (wasnt doing anything unusual - just using firefox and audacity) ....didn't catch the error messgae, and didn't think much of it - just went and rebooted - trying to boot the linux drive from GRUB (I also have Windows on another HD) - it wouldn't load.  Neither would the recovery option.  

Booted from the Ubuntu 12.04 system disk, and used the "Try Ubuntu" option.  Couldn't even mount the drive Ubuntu is located on, though it shows up in fdisk -l.  

Ran ran "sudo fsck -t ext4 -f /dev/sdb1 from terminal and got this message - 

JBD: Failed to read block at offset 8480
fsck.ext4: Input/output error while recovering ext3 journal of /dev/sdb1
/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: ********** WARNING: Filesystem still has errors **********

This allowed me to at least mount the drive, but not access much or boot from it - always got an error saying it couldn't read file - kernel must be loaded first when I tried to boot.

Then ran sudo fsck -t ext4 -y /dev/sdb1 - and it was fixing a ton of errors overnight like this in pass one - 
Inodes that were part of a corrupted orphan linked list found.  Fix? yes
Inode 56885569 was part of the orphaned inode list.  FIXED.  There was around 100 of those fixed.

Went on to pass two and it was fixing a lot more errors...


Entry 'ksocket-ehah' in /tmp (9961473) has an incorrect filetype (was 2, should be 6).  Fix? yes  (ehah is my username on system btw)

A lot of those  errors don't even show an entry name or directory location - just says  Entry '...' in ??? and said its missing '..." in a directory Inode.


After pass two completed, it gave an error that said "resize inode not valid "  and re-ran pass one.  Not sure what happened after this point (I was just letting it run - the whole process took around 18 hours) - but the final result was - 


/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED ***** /dev/sdb1: 262033/121610240 files (0.6% non-contiguous), 45779164/486412288 blocks.

Still won't boot - and won't mount anymore when I'm using the Ubuntu live CD.  

No backup.  Any ideas how to get this working again, or at least save as much data as possible?

The drive was always unmounted when I was using the fsck command.

When I try to mount the drive from the terminal , I get mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Fdisk -l shows the following (sda1 is a seperate drive with Windows on it, that runs fine.)

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  2930255999  1465127968+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00003767

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  3891300351  1945649152   83  Linux
/dev/sdb2      3891302398  3907024895     7861249    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5      3891302400  3907024895     7861248   82  Linux swap / Solaris

---

### Post by TheFu on 2013-08-21
Looks like you've done all the things you can - something about the hardware is bad. HDD, cable, controller, SATA port, PSU  ... something.
a) Do the log files show anything to pinpoint the HW issue?

b) I'd try swapping the SATA cable out and using a different SATA port on the MB or controller. Doubtful it will work, but ... gotta try.

c) You are in data save mode now.
[LIST=1]
[*]Stop using the HDD; disconnect the power cable.
[*]Buy a new HDD at least as large connect it up. Consider getting 2 (the xtra is for backups!)
[*]Reconnect the old drive - SATA is best, USB3, eSATA are good, USB2 sucks.
[*]Use ddrescue to mirror the entire HDD, not just the partitions. /dev/sda - the entire device.
[*]The only thing you should do with that old HDD is mirror from it. NOTHING else.
[/LIST]

For large HDDs and 4K sector HDDs, **don't use fdisk again.**  It doesn't automatically do some things you want handled. Use **gparted** or **parted** instead.

It appears you are corrupting/changing data with every fsck run. This may be helping or not.  testdisk and photorec might let you recover some files. It will probably be painful.

Having a versioned backup at a time like this would mean this was a minor inconvenience. I've seen average 2TB HDDs for less than $100. If you've spent over 3 hours on this, having that backup would have been cheaper for most people. Just a thought.  I'll also say that I do not backup everything, but I do backup everything important.

---

### Post by russ3 on 2013-08-21
Think I figured this out myself - found an article about restoring from a backup superblock - and that seems to have worked so far (Ie - booted fine, doesn't seem to be any missing/corrupt files).  Hope it holds up!

Didn't even see the reply above while I was typing this one - probably a good time to get an new drive and back-up what I have now huh?

---

### Post by TheFu on 2013-08-21
If the superblock became corrupted, that isn't good. 
Is the root cause known or is this just a quick fix for the next 3 days?

Backups. Know them. Love them. Do them. Sleep better.

---

### Post by russ3 on 2013-08-21
Don't know the root cause for sure - but seems like the original superblock became corrupted when the system unexpectably crashed.  And like I said don't know what caused the crash.  Cash is tight, but probably should go pick up a new drive and do a backup soon.

---

