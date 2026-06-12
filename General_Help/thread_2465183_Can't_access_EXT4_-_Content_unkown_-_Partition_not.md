---
title: "Can't access EXT4 - Content unkown - Partition not found?"
date: 2021-07-24
forum: General Help
---

### Post by halluz on 2021-07-24
Hello everybody , i can no longer access my almost full 10 TB WD shucked external HDD.
I formatted it before shucking ~1 month ago with:
```

sudo mkfs.ext4 -m 0 -T largefile4 -L <drivename> /dev/sdb

```


I solved the WD 3.3V pin issue with non conductive tape.
It was inside a SATA to USB SCSI Adapter first and later directly connected via SATA inside the PC. Everything was working fine.
One day (after some shutdowns) i noticed that i can't access the stored files anymore.

[Attachements]("https://imgur.com/a/sGjhSI2")
Images(in that order)
1. Gnome Disks looks like this
2. testdisk, if i chose "no partition"
3. testdisk if i chose efi gpt (nothing happens if i press enter):i
4. fsck (same without -vn):
5. smart
6. i run smart self test (short):
7. testdisk change type to "ext4" (nothing found with "list" or "superblock"):
8. mke2fs

Also tried [this]("https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/") without success (superblock numbers not working):

I've read somewhere, that its possible to recover files with cloning, but i dont have 10tb of free storage now.

Any other ideas? Thank you!

---

### Post by TheFu on 2021-07-24
Always, always, lay down a partition table.  It appears you may not have done that based on pointing at sdb, instead of one of the partition like sdb3 or sdb1 or sdb9.   Never format an entire storage device, always put a partition table down first - GPT unless there is a technical reason that cannot be used. All sorts of tools won't work without a partition table.

Besides that, **hopefully, you have great backups**.  All storage is going to fail. Some before we get it, some after a few days, some after a few months, some around the time the warranty ends and others 10-15 yrs later.  We all hope for the 15 yr storage, but sadly, that isn't the rule. Backups are only optional for data you don't care about. This is a universal truth for all storage. You probably already know these things. Lurkers in 4 yrs may not.

I assume you've validated all the funky electrical stuff that was hacked together for the shucking to work? Can you put it back into the enclosure and try it that way? Is that possible?

I'm not a fan of GUI tools.  They are limited in capability and often lie.  Typically, the GUI version of any tool provides 20% of the features when compared to the command line version.

First, run some non-GUI tools so we can get some facts. Start with these:
```
sudo fdisk -l
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
Also, post using code tags so the columns line up just like they do in the terminal.  [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) 
It would be nice if you could remove any "loop" devices from the **fdisk** output. Those have nothing at all to do with real storage.  The **lsblk** command above blocks 'loop' devices to get right to the point.

It would be kind to use attachments, not inline images, for people who pay for their connection by the byte in the first post. Can you please edit it?

---

### Post by bcschmerker on 2021-07-24
:frown:  **The Western Digital® WD100EZAZ may have a corrupted partition table.**  TestDisk 7.1 read the HDD as a 19,532,873,728-sector ext4 drive, but e2fsck.ext4 ran into, I'm estimating, the corrupted partition table, therefore the I/O error attempting to open /dev/sdb.

---

### Post by TheFu on 2021-07-24
GPT has a primary and backup copy of the partition table at opposite ends of the HDD.  It is very unlikely for both to be missing, since they are physically "far" apart on the disk.  That means the issue is power, cable, or disk controller (either in the PC or inside the drive itself).

Try changing those things out.

---

### Post by halluz on 2021-07-24
I've put it back into the USB adapter/enclosure. Same Problem.

No entry for the drive with sudo fdisk -l.

```

lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME          SIZE TYPE FSTYPE MOUNTPOINT
sdb           9,1T disk
   
```
 
However, suddenly i can use testdisk analyse. and it says:

```

Disk /dev/sdb - 10000 GB / 9313 GiB - CHS 9537504 64 32
Analyse cylinder    69/9537503: 00%
Read error at 68/63/32 (lba=141311)

```

changing type to ext4 and clicking on "List and copy files":
```

TestDisk 7.1, Data Recovery Utility, July 2019



   P ext4                     0   0  1 9537503  63 32 19532808192






Can't open filesystem. Filesystem seems damaged.

```

---

### Post by TheFu on 2021-07-24
He's dead, Jim.  Sorry.
If you had backups of the drive or the partition table, there might be something more to try. Without any partition table, I think there is little to be done. Learn from this. If you are willing to lose the data in the first 2M and last 2M of storage, you could slap a partition table down with a single partition. Do not format anything and give some data recovery tools a chance.  For that amount of disk, it could take a few weeks, depending on the number of problems with whatever is causing the read problems.  You'll need another disk the same size or larger to restore any found files onto.

Google for "ubuntu data recovery", you'll find a wiki page about it.  This will be extremely painful.  Filenames will not be recovered. All recovered files will be assigned numeric names and sometimes different versions of the same file will be found, so you'll have to manually decide which to keep.  I've done this with 100G of files and I considered that to be painful.  Can't imagine doing it on 10TB of files.  Having backups is so much easier.

---

### Post by oldfred on 2021-07-26
If you just wrote data to drive like sdb, then the normal locations on the drive for partition table has random data in it.
And then all the partition tools will fail.

You in effect have a very large floppy drive configuration. Floppy drives had no partitions.
None of the standard partition tools will then work.

Not sure this will work or not, may need sdb, not fd0:
sudo udisksctl mount -b /dev/fd0

[https://unix.stackexchange.com/questions/346826/is-it-ok-to-mkfs-without-partition-number](https://unix.stackexchange.com/questions/346826/is-it-ok-to-mkfs-without-partition-number)

---

### Post by ActionParsnip on 2021-07-26
Why do you not have backups? Is the data not valuable to you?

---

### Post by halluz on 2021-08-22
> **ActionParsnip said:**
> Why do you not have backups? Is the data not valuable to you?
it's not that valuable really, the drive was used for proof of space(chia), so no personal data.... 

Sorry, i was frustrated and just put the drive away for a few weeks, now my motivation is back and i try to format it.
I realize now, that the drive could be dead and i can throw it in the trash!?  Because i can't format it. Input/output errors.....

Does somebody have any suggestions how to make that disk work again?

---

### Post by oldfred on 2021-08-22
If no data to worry about, you can zero out partition table & see if you can create a new one.
This was for the old MBR(msdos) partitions, similar to reusing a flash drive:
Reset USB flash that was dd'd to make it usable again, reuse
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266) & 
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive) & 
[https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection](https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection)

Zero out MBR and partition table
dd if=/dev/zero of=/dev/sdX bs=512 count=1 # where sdX is your drive. Double check that it is the drive you want as on reboot sometimes drive order changes. And damage to a working drive about impossible to repair.

Not sure if that MBR only erase works with gpt as it has table at both beginning (after MBR) and at end of drive. But if MBR is blank, you probably can then use gparted and under device select gpt and it will warn you that it will erase drive (as it really just erases partition table).
[https://unix.stackexchange.com/questions/167500/using-dd-to-zero-a-gpt-table-from-disc-how-many-bytes-to-write](https://unix.stackexchange.com/questions/167500/using-dd-to-zero-a-gpt-table-from-disc-how-many-bytes-to-write)
[https://www.rodsbooks.com/gdisk/wipegpt.html](https://www.rodsbooks.com/gdisk/wipegpt.html)

Gdisk may see drive as only MBR and offer to convert also.

---

