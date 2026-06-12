---
title: "Mount file using loop / cloop"
date: 2007-08-01
forum: General Help
---

### Post by crowndip on 2007-08-01
Hello,

I created a copy of my windows computer partition ( NTFS ) with dd command. Now I want to copy the file to my ubuntu feisty computer.

I suppose I can mount it using:

**sudo mount -o loop -t ntfs imagefile.img /mnt/windisk/** --- is this correct ?

I only want to be able to read the data and they are well compressible. So my question is:

If I have the same file compressed by gzip or bzip2 (windisk.gz or windisk.bz2) , **can I mount the compressed file using cloop ? How would I do this ?**

Thanks a lot
Filip

---

### Post by crowndip on 2007-08-03
Hello,

The command:
[B]
sudo mount -o loop -t ntfs imagefile.img /mnt/windisk/[/B][COLOR="Red"] does not work[/COLOR]

It gives me some error about the file not being a correct block device. I found somewhere that I have to give an offset as parametr but how and which one ?

The file is an exact copy of windows partition done as **dd if=/dev/hda1 of=/imagefile.img**

Anyone knows ?

Thanks
Filip

---

### Post by crowndip on 2007-08-04
hello,

I find the way how to mount it :

 mount -t auto -o loop,errors=recover hda3file ./test

but it's only read-only

[  778.554427] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[  778.554565] NTFS-fs warning (device loop0): read_ntfs_boot_sector(): Hot-fix: Recovery of primary boot sector failed: Read-only mount.
[  778.554570] NTFS-fs warning (device loop0): read_ntfs_boot_sector(): Using backup boot sector.
[  778.579869] NTFS volume version 3.1.

---

### Post by Bubbel on 2008-02-19
Shouldn't you use ntfs-3g as type (i.e. -t ntfs-3g) ?
the ntfs kernel driver (thus -t ntfs) is called upon when you use -t auto. This driver only supports read-only ntfs support.

ntfs-3f does the (writing) job. It's installed in the latest release (7.10) by default.

success, Bubbel

---

