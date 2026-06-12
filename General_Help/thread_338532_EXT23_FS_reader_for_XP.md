---
title: "EXT2/3 FS reader for XP?"
date: 2007-01-14
forum: General Help
---

### Post by winter_mute on 2007-01-14
So I feel kinda bad asking this here, but I'm hoping I won't get smote for it.  Anyways, I need to run dual-boot on my laptop because of school apps.  And I'd like to only have one copy of music on my laptop, to save space since I have two OS'.  I figure the best option would be to get an EXT3 file reader for XP, but the last time that I used one, it kept destroying just the partition that Ubuntu was stored on.  Which also stored GRUB.  Which was just a minor irritant, having to reinstall every time I wanted to reboot.  Does anyone here know of a good FS reader for EXT2/3, and a way to stop XP from killing Ubuntu?  I'd really appreciate any help I can get here.

---

### Post by Ramses de Norre on 2007-01-14
[This](http://www.fs-driver.org/) one works ok for me.

---

### Post by winter_mute on 2007-01-15
Okay, so that's what I've been using... Hopefully I can figure out the permissions to give it some better ... lack of deleation / corruption of my Ubuntu partition.

---

### Post by orb9220 on 2007-01-15
Nope from their FAQ:

> What features are *not* supported?

    * Access rights are not maintained. All users can access all the directories and files of an Ext2 volume. If a new file or directory is created, it inherits all the permissions, the GID and the UID from the directory where it has been created. With version 1.10a of the software there is one exception to this rule: a file (but not a directory) the driver has created always has cleared "x" permissions, it inherits the "r" and the "w" permissions only. See also section "What limitations arise from not maintaining access rights?".
    * The driver treats files which have got a file name beginning with a dot "." character like other files, but not as hidden files.
    * The driver does not allow accessing special files at Ext2 volumes, the access will be always denied. (Special files are sockets, soft links, block devices, character devices and pipes.)
    * Neither different code pages nor UTF-8 encoded file names are supported. The driver always uses the current code page of Windows.
    * Alternate 8.3-DOS names are not supported (just because there is no place to store them in an Ext2 file system). This can prevent legacy DOS applications, executed by the NTVDM of Windows, from accessing some files or directories.
    * Currently the driver does not implement defragging support. So defragmentation applications will neither show fragmentation information nor defragment any Ext2 volume.
    * This software does not achieve booting a Windows operating system from an Ext2 volume.
    * LVM volumes are not supported, so it is not possible to access them.


Still a great program which I use also on my dual setup.

---

### Post by gwpritch on 2007-01-15
If you feel like a little repartitioning you can create a shared fat32 partition to store your music. It can be accessed by both XP and Linux.

---

### Post by louieb on 2007-01-15
Here is an ext2  read only drive for windows I've used. But now like orb9220 and Ramses de Norre I use ext2fs and have not had a problem with it.
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm]("http://uranus.it.swin.edu.au/%7Ejn/linux/ext2ifs.htm")

---

