---
title: "Second hard drive, Superblock become corrupt.."
date: 2007-01-02
forum: General Help
---

### Post by yawnster on 2007-01-02
Howdy guys..

I woke up this morning, turned on the box, met by a disc error screen.. It told me I had a bad superblock and needed to run **fsck** to fix it, I ran the command.. Rebooted.. And when I got into Ubuntu my second hard drive was accessible.. R/O though.. 

(Its an ext3 30gb drive.. usually R/W.. mounted through my home folder using /etc/fstab)..

The **dmesg** says..

```
[17180476.748000] EXT3-fs: hdb1: couldn't mount because of unsupported optional features (80008000).
```

and **syslog**  says.. 

```
Jan  2 11:34:55 alex-ubuntu kernel: [17180476.748000] EXT3-fs: hdb1: couldn't mount because of unsupported optional features (80008000).
```

When I run gparted I cannot see a filesystem and it says its corrupt.. Which command should I try to use to repair an ext3 filesystem.. because fsck is saying that only only ext2..

I would really love to get the data off the drive as it contains my Music, Pictures, Work etc.. But I do have some backups that are around a month old though.. So all wont be lost if I cant..

Thanks in advance.. Alex

---

### Post by kidders on 2007-01-02
Hi there,

Have you done anything strange lately? My only experience of that error has to do with doing things like creating a filesystem with a very new "mkfs" and mounting it with a very old "mount".

If you can mount your filesystem in read only mode, I would copy all the stuff off it first, and play around with it afterwards.

**Edit:** > fsck is saying that only only ext2Ext3 _is_ Ext2 (journalised Ext2, that is). :-)

---

### Post by ikonia on 2007-01-02
fsck is for ext2 and 3

assuming your problem disk/partition is /dev/sda1 for example

run 

fsck -n /dev/sda1

this will not alter anything but report back errors on the file system.

Read/understand the errors and fix them

remember to fsck a partition not a disk

---

### Post by yawnster on 2007-01-02
Hmm... Thing is I rebooted to see if I can get it into R/W.. All last night I was doing web development, so a lot of save and edit etc..

This is the error message I get when running **fsck**

```
alex@alex-ubuntu:~$ sudo fsck /dev/hdb1
Password:
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext3: Filesystem revision too high while trying to open /dev/hdb1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```

Should I go ahead and try with an alternative superblock? (Same error as when -n is passed)..

When running **mount -a** I get this..

```
alex@alex-ubuntu:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The line for this hard drive in /etc/fstab is..

```
/dev/hdb1       /home/alex/Data ext3 defaults    0    0
```

I have been using this hard drive in this form for about 3 months now, without any problems.. Just has suddenly occurred this morning..

Thanks again.. Alex

EDIT: I ran the command.. **sudo e2fsck -b 1893 /dev/hdb1** as the error message said.. But I now get this error message..

```
alex@alex-ubuntu:~$ sudo e2fsck -b 8193 /dev/hdb1
e2fsck 1.39 (29-May-2006)
e2fsck: Bad magic number in super-block while trying to open /dev/hdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```

---

### Post by kidders on 2007-01-02
Yuk! :-(

> **yawnster said:**
> fsck.ext3: Filesystem revision too high while trying to open /dev/hdb1
The filesystem revision is apparently too high for this version of e2fsck.This is where the weird message about unsupported features is coming from, and the reason I wondered about odd things you might have been doing recently. I suppose it could just be a chance corruption.

Before trying alternate superblocks, see if you can get Ubuntu to list them for you first. Don't just guess at locations! Also, I really would recommend explicitly performing read only mounts ... just in case.

---

### Post by ikonia on 2007-01-02
ok the fsck.ext3: Filesystem revision too high while trying to open /dev/hdb1
error.

worrying.

whats the layout of this box ? is it a 6.06 box thats been updated to 6.10 ? a 7.X box ? etc etc.

Have you got any custom repo's on there or manually built any packages.


Can you still access the physical device with other tools (eg fdisk -l /dev/hdb)

if you manage to mount it read only - back it up somewhere quick !

What does the syslog say ?
Does dmesg make any hardware complaints ?

---

### Post by yawnster on 2007-01-02
I believe its a straight 6.10 box.. It did have 6.06 on it before, but as I use the second drive as a data drive I just formatted the boot drive and put 6.10 on..

I don't have custom packages that I would think are interfering with this.. I mean Beryl installed, Skype and I think that's about it from custom repositories..

**sudo fdisk -l /dev/hdb** bring up this..

```
alex@alex-ubuntu:~$ sudo fdisk -l /dev/hdb

Disk /dev/hdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3738    30025453+  83  Linux

```

Which is a good sign that the device is not totally dead.. 

How would I get Ubuntu to list the superblocks to try? 

Thanks.. Alex..

PS.. [Output of syslog and dmesg..]("http://www.yawnster.com/random/error.txt")

---

### Post by yawnster on 2007-01-02
hmm.. running **fdisk -l**.. The ID Numbers are the same? Is this a problem, I am assuming that ID's are supposed to be unique, and maybe this is a problem?

```
alex@alex-ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9602    77128033+  83  Linux
/dev/hda2            9603       10011     3285292+   5  Extended
/dev/hda5            9603       10011     3285261   82  Linux swap / Solaris

Disk /dev/hdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3738    30025453+  83  Linux

Disk /dev/sda: 1026 MB, 1026555904 bytes
16 heads, 32 sectors/track, 3916 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916     1002480    e  W95 FAT16 (LBA)
```

Looking over [this wikipedia]("http://en.wikipedia.org/wiki/Unix_File_System") article, it seems like there is a backup copy of the superblock somewhere.. does anyone know how to access and reinstate it?

Thanks again, Alex..

---

### Post by kidders on 2007-01-03
> **yawnster said:**
> hmm.. running **fdisk -l**.. The ID Numbers are the same? Is this a problem, I am assuming that ID's are supposed to be unique, and maybe this is a problem?The ID numbers you're referring to are probably the filesystem type flags (82, 83, etc.), which are intended to indicate the purpose of a disk partition, I suppose. They're not intended to be unique.

> **yawnster said:**
> it seems like there is a backup copy of the superblock somewhere.. does anyone know how to access and reinstate it?The best way to find alternate superblocks (there should be a whole string of them) is to recreate a filesystem, as you did originally. Use mkfs's **-n** option to "pretend" to create one, using the same block size/etc. as the corrupted filesystem, and note the locations of the backup superblocks.

Once you have the list, try a few of them, and see what happens.

---

### Post by Bigbluecat on 2007-01-03
I don't know if this will help but on the GParted Live CD there is a very useful program called Testdisk.

Open a terminal and type Testdisk.

Since you are running a LiveCD the drives are not mounted so all kinds of things can be repaired.

I used this to recover a corrupted partition table.  It was a windows crash problem not Ubuntu but the utility was very powerful and intuitive to use. My C: partition vanished and all the windows files were on D:. This program recovered the partition and put all the files back.

---

