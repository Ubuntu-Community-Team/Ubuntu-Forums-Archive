---
title: "Can't mount external USB drive, inode table conflict?"
date: 2007-02-05
forum: General Help
---

### Post by sethj2 on 2007-02-05
6.10, Kernel 2.6.17-10-generic

I am suddenly unable to mount my external 250gb external SATA HD. It is detected by the disk mounter, but when I try to mount it (using disk mounter or mount in terminal) the following error appears... 


"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted

mount: wrong fs type, bad option, bad superblock on /dev/sde1,
missing codepage or other error
in some cases useful info is founf in syslog - try
dmesg | tail or so

error: could no pmount "

dmesg | tail returned:

[17189325.396000] sde: assuming drive cache: write through
[17189325.400000] SCSI device sde: 488397168 512-byte hdwr sectors (250059 MB)
[17189325.400000] sde: Write Protect is off
[17189325.400000] sde: Mode Sense: 00 38 00 00
[17189325.400000] sde: assuming drive cache: write through
[17189325.400000] sde: sde1
[17189325.408000] sd 5:0:0:0: Attached scsi disk sde
[17189325.408000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[17189326.420000] EXT2-fs: corrupt root inode, run e2fsck
[17189513.356000] EXT2-fs: corrupt root inode, run e2fsck


Gnome partition editor lists the disk and shows the:

first sector as 63, and
last as 488392064
total as 488392002


Testdisk /list returned: `

Partition sector doesn't have the endmark 0xAA55
Disk /dev/sdd - 250 GB / 232 GiB - CHS 30401 255 63
Partition Start End Size in sectors
1 P Linux 0 1 1 30400 254 63 488392002

e2fsck -p returned:

seth@ubuntoshiba:~$ e2fsck -p /dev/sdd1
/dev/sdd1 contains a file system with errors, check forced.
/dev/sdd1: Group 2's inode table at 65538 conflicts with some other fs block.

/dev/sdd1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

e2fsck returned:

e2fsck 1.39 (29-May-2006)
/dev/sdd1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Group 2's inode table at 65538 conflicts with some other fs block.
Relocate<y>?



THANK YOU!

---

### Post by dcstar on 2007-02-07
> **sethj2 said:**
> 
.........
1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

e2fsck returned:

e2fsck 1.39 (29-May-2006)
/dev/sdd1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Group 2's inode table at 65538 conflicts with some other fs block.
Relocate<y>?


THANK YOU!

Well, what happens when you actually let fsck fix the errors it has found?

---

### Post by sethj2 on 2007-02-12
"/e2fsck -v -y /dev/sdb1"  yields:

/dev/sdc1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Group 2's inode table at 65538 conflicts with some other fs block.
Relocate<y>? 
. 
.
.
.

Group 1863's block bitmap at 61046784 conflicts with some other fs block.
Relocate? yes

Group 1863's inode bitmap at 61046785 conflicts with some other fs block.
Relocate? yes

Root inode is not a directory.  Clear? yes

At this point it hangs, not sure what its doing but the HD is definitely busy.

Thanks for the help!

---

### Post by dcstar on 2007-02-12
> **sethj2 said:**
> "/e2fsck -v -y /dev/sdb1"  yields:

/dev/sdc1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Group 2's inode table at 65538 conflicts with some other fs block.
Relocate<y>? 
. 
.
.
.

Group 1863's block bitmap at 61046784 conflicts with some other fs block.
Relocate? yes

Group 1863's inode bitmap at 61046785 conflicts with some other fs block.
Relocate? yes

Root inode is not a directory.  Clear? yes

At this point it hangs, not sure what its doing but the HD is definitely busy.

Thanks for the help!

Just let it finish, it may take a while to process everything.

---

