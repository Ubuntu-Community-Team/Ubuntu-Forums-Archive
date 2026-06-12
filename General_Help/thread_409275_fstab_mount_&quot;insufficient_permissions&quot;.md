---
title: "fstab mount &quot;insufficient permissions&quot;"
date: 2007-04-14
forum: General Help
---

### Post by gregconquest on 2007-04-14
In trying to open a vmx file with VMware Player in kubuntu, I get the error message:
```
Error while opening virtual machine . . .
Insufficient permissions to access the file.
```
I think I have that particular partition mounted incorrectly.

In my fstab, I had:
```
# /dev/sdb5	LinDATA
UUID=8bebaccc-bb8a-4d07-8de5-0b170299706b /media/LinDATA(sdb5) ext3    defaults        0       2
```
I looked around at fstab tutorials, and I figured I needed to change the "nouser" aspect of "defaults" to "user", like so:
```
# /dev/sdb5	LinDATA
UUID=8bebaccc-bb8a-4d07-8de5-0b170299706b /media/LinDATA(sdb5) ext3    rw,suid,dev,exec,auto,user,async        0       2
```
but still I get the same error.

Can someone tell me what I'm doing wrong?

Thank you.
Greg Conquest

---

### Post by Scunizi on 2007-04-14
Take a look at my fstab for the ext3 line and mirror that.  Feasibly it should fix it.  I had to tinker with it to get it to work.

Note:  things might look a little different because I'm on Dapper and it doesn't use uuid functions.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               reiserfs notail          0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/hda1	vfat	user,auto,fmask=0111,dmask=0000
/dev/sda2	/media/sda2	ext3	rw,user	0	1

```

---

### Post by gregconquest on 2007-04-16
Thanks Scunizi  ,

I tried this, but it didn't help me. I may be having problems other than mounting options that are causing the error, though. Thunderbird also won't launch always saying another instance is running and I have to shut it down first or reboot. This happens at every launch -- even after a fresh boot. I may need to track down that problem first . . .

Regarding fstab mount options, though, I still don't know how to mount that drive. The tutorials I've seen, [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html"), for example, are understandable, but there are still multiple conceivable options for any situation **and very few examples listed**.

I think any useful tutorial should list common options for:
- a data partition in ext3 format
- another Linux OS partition
- NTFS as read-only
- fat32 partitions common to Linux and Windows
- . . .
The tuxfiles' examples are limited to to a floppy and a CDRom.

Greg

UPDATE: I searched for "Mozilla-Thunderbird is already running" and I was led back to my own posts:
[http://kubuntuforums.net/forums/index.php?topic=13426.msg53719#msg53719]("http://kubuntuforums.net/forums/index.php?topic=13426.msg53719#msg53719") and [http://ubuntuforums.org/showthread.php?p=2107144#post2107144%22]("http://ubuntuforums.org/showthread.php?p=2107144#post2107144%22")

Then the reason Thunderbird was displaying the same error message then was because I didn't have the partition where the profile and data were located mounted correctly in fstab! Oh, and now? I'll list this out.

The working recommendation for ubuntu was:
/dev/sdb1   /media/SATA320FAT32  vfat   iocharset=utf8,umask=000   0   0

What I had in kubuntu's fstab for this issue here was:
# /dev/sdc1	O_LinWin
UUID=12D7-0200  /media/O_LinWin(sdc1) vfat    defaults,utf8,umask=007,gid=46 0       1

I just changed this to:
# /dev/sdc1	O_LinWin
UUID=12D7-0200  /media/O_LinWin(sdc1) vfat    iocharset=utf8,umask=000 0       0

Yet I am still getting the same error message. I am almost lost now. It seems a problem i am having that I should clear up first is the correct mounting options in fstab for the Thunderbird issue. Then, once that is working *again*, I should try again with the VMware Player and the ext3 data partition where my WinXPPro virtual machine resides.

Does anyone see my mistake(s)?

---

