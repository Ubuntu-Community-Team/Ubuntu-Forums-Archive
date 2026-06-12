---
title: "Transferring Mac files to Linux"
date: 2014-01-05
forum: General Help
---

### Post by ron177 on 2014-01-05
Dear all,

I have a series of files and folders in a Mac partition (hfs+) which I  have difficulty transferring to a Linux partition (ext4). These are some  photos (jpg format for the most part), email files (.mbox format), and  videos (avi format) which for some reason I cannot copy/paste from hfs+  to ext4 (even after I took over the "ownership" of the partition). More  importantly, I cannot view the videos or the photos or the emails. Is  there anyway someone can help me with (a) transferring them to ext4 and  (b) viewing them in an ext4 partition?

Many thanks in advance.

---

### Post by tgalati4 on 2014-01-05
It should be plug-and-play.  If it is not, then you have a problem.

Open a terminal and post the output of:

```
sudo fdisk -l
```

What hfs utilities do you have on your system?

```
apropos hfs
```

What hfs utilities are available to install on your system?

```
apt-cache search hfs
```

---

### Post by ron177 on 2014-01-05
Thanks for your message. Here's what you requested:

The output for the following code (sudo fdisk -l) is:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x510739f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   475286374   237539763+   7  HPFS/NTFS/exFAT
/dev/sda3       924190720   976773167    26291224   12  Compaq diagnostics
/dev/sda4       475287550   924190719   224451585    5  Extended
/dev/sda5       475287552   911902719   218307584   83  Linux
/dev/sda6       911904768   924190719     6142976   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99f0b0c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625142447   312571192+  af  HFS / HFS+

the output for the following code (apropos hfs):

genisoimage (1)      - create ISO9660/Joliet/HFS filesystem with optional Ro...
tc-hfsc (8)          - Hierarchical Fair Service Curve's control under linux

the output for the following code (apt-cache search hfs):

genisoimage - Creates ISO-9660 CD-ROM filesystem images
hfsplus - Tools to access HFS+ formatted volumes
hfsutils - Tools for reading and writing Macintosh volumes
libcephfs-dev - Ceph distributed file system client library (development files)
libcephfs1 - Ceph distributed file system client library
libcephfs1-dbg - debugging symbols for libcephfs1
libhfsp-dev - Library to access HFS+ formatted volumes
libhfsp0 - Shared library to access HFS+ formatted volumes
parted - disk partition manipulator
squashfs-tools - Tool to create and append to squashfs filesystems
squashfs-tools-dbg - Tool to create and append to squashfs filesystems (debug)
sshfs - filesystem client based on SSH File Transfer Protocol
sshfs-dbg - filesystem client based on SSH File Transfer Protocol (with debugging symbols)
classmate-initramfs - classmate specific initramfs settings
dmg2img - Tool for converting compress dmg files to hfsplus images
hfsprogs - mkfs and fsck for HFS and HFS+ file systems
hfsutils-tcltk - Tcl/Tk interfaces for reading and writing Macintosh volumes
libghc-hfuse-dev - Haskell binding for the Linux FUSE library
libghc-hfuse-doc - Haskell binding for the Linux FUSE library; documentation
libghc-hfuse-prof - Haskell binding for the Linux FUSE library; profiling library
libhfstdc++6-4.6-dbg-armel-cross - GNU Standard C++ Library v3 (debugging files)
libhfstdc++6-armel-cross - GNU Standard C++ Library v3 (hard float ABI)
ltsp-livecd - starts an LTSP live server on an Ubuntu livecd session
p7zip-full - 7z and 7za file archivers with high compression ratio
partimage - backup partitions into a compressed image file
partimage-doc - Partition Image User Documentation
rdiff-backup-fs - Fuse filesystem for accessing rdiff-backup archives
sbackup-plugins-fuse - Simple Backup Suite FUSE plugins
testdisk - Partition scanner and disk recovery tool

---

### Post by tgalati4 on 2014-01-05
Install a few utilities because you are probably going to need them:

```
sudo apt-get install hfsprogs hfsutils-tcltk hfsplus hfsutils
```

Unmount the drive:

```
sudo umount /dev/sdb1
```

Check it:

```
sudo fsck /dev/sdb1
```

Remount it:

```
sudo mount -a
```

Change directory into the drive and post l*s -la* of a typcial directory of files that you are having problems with:

```
cd /media
ls
cd (mac drive label)
cd (mac directory with files you are having problems with)
ls -la
```

If everything checks out OK, then it could be a MIME (file type) problem.  [https://help.ubuntu.com/community/AddingMimeTypes](https://help.ubuntu.com/community/AddingMimeTypes)

---

