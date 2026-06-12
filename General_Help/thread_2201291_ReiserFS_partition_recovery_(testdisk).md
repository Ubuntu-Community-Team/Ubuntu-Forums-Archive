---
title: "ReiserFS partition recovery (testdisk?)"
date: 2014-01-23
forum: General Help
---

### Post by tCabot on 2014-01-23
Hi!

I would be very grateful for any help with the following problem. I am really desperate to recover my files so any solutions are welcome!

My old laptop which had a dual boot configuration has died. The hard drive was partitioned with NTFS partition followed by 2 ReiserFS partitions and some swap space.
I removed the old hard drive and put it into an external disk enclosure to access some of my data from one of the ReiserFS partitions on my girlfriend's laptop (running Ubuntu). The partition mounted ok and I got the file I needed. However, after unmounting the drive the partition table seems to have corrupted. Now when I connect the drive only the NTFS partition is recognised & mounted.

I installed testdisk and analysed the drive. Testdisk has correctly identified all partitions' locations, however, it seems to think that the 2 reiserFS partitions are Ext4 and are corrupt. I tried changing the fs type but I do not get ReiserFS as an option in testdisk menu! =(
I even tried downloading progsreiserFS and compiling testdisk with libraries from them, but still it looks like ReiserFS is not supported by my testdisk. Please help!

Are there any ways to include the Reiser support in testdisk or any alternatives to testdisk? I know there was a way to re-write the ReiserFS superblock with another program but it requires quite complex inputs (for a newb like me) like block sizes etc.

PS I've tried running photorec and it seems to be able to recover some files under a "not ext fs" option. I would, however, much prefer to just restore the whole partition rather than each individual file.


Thank you,

Chavez.

---

### Post by dragonfly41 on 2014-01-23
Before you go much further perhaps you should look through the testdisk forum.

[http://forum.cgsecurity.org/phpBB3/help-with-external-hd-and-reiserfs-t2409.html](http://forum.cgsecurity.org/phpBB3/help-with-external-hd-and-reiserfs-t2409.html)

If the files you are trying to recover are very valuable you might consider cloning your failed drive onto another drive .. as an insurance policy.

You will need space for recovery of any files .. if it is not a simple fix.

---

### Post by tgalati4 on 2014-01-23
reiserFS support was dropped a while ago, so it's possible that older tools would include reiserFS detection.  Try loading an older Live CD and with an ethernet connection, load testdisk from an older repository.  You will have to do some research to find the latest Ubuntu that supported reiserFS.

ReiserFS tools may still be available.  On my 12.10 system:

tgalati4@Mint14-Extensa ~ $ apt-cache search reiser
libaal-dev - Reiser4's application abstraction library
libreiser4-dev - Reiser4's filesystem access and manipulation library
**reiser4progs** - administration utilities for the Reiser4 filesystem
**reiserfsprogs** - User-level tools for ReiserFS filesystems
chiark-scripts - chiark system administration scripts
fstransform - Tool for in-place filesystem conversion
gpart - Guess PC disk partition table, find lost partitions
mountmanager - User-friendly management of disks and partitions
partimage - backup partitions into a compressed image file
partimage-doc - Partition Image User Documentation
partitionmanager - A partition management utility
testdisk - Partition scanner and disk recovery tool

Make sure you have the correct libraries loaded:

tgalati4@Mint14-Extensa ~ $ testdisk -v
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Version: 6.13
Compiler: GCC 4.7
Compilation date: 2012-10-01T13:00:04
ext2fs lib: 1.42.5, ntfs lib: libntfs-3g,** reiserfs lib: none**, ewf lib: none
OS: Linux, kernel 3.5.0-39-generic (#60-Ubuntu SMP Tue Aug 13 18:33:05 UTC 2013) x86_64

No libraries, no detection.

---

