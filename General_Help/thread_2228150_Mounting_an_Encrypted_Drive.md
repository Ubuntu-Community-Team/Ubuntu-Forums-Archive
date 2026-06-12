---
title: "Mounting an Encrypted Drive"
date: 2014-06-05
forum: General Help
---

### Post by craig10 on 2014-06-05
Hi there,

I am trying to mount an encrypted drive read-only so that I can try and use Photorec to recover a file that was truncated by a Gedit plug-in. However, I'm obviously doing it wrong.

I have a laptop running Ubuntu 13.10. It has two drives: /dev/sda (the boot drive) is a 120 GB SSD, and /dev/sdb (secondary drive, where I store most of my data) is a 500 GB HDD. The secondary drive is encrypted. I'm new to running my own Linux machine, so right now this machine is pretty much running various defaults. During the set-up process I was asked if I wanted to encrypt the secondary drive and I selected yes, and created a pass phrase. I believe this was encrypted using LUKS. Each time I log in I must enter the pass phrase to access the secondary hard drive. This is the way I want it, so everything is good from that perspective.

Looking at the properties for the drive shown in the file browser (which I believe is Nautilus) told me that the drive is "ext3/ext4". I found it odd that both are shown, but that's what it shows. So I tried mounting it like this:

```
 sudo mount -t ext4 -o ro,noload /dev/sdb /romount
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The directory /romount does exist. I also tried /dev/sdb1:

```
 sudo mount -t ext4 -o ro,noload /dev/sdb1 /romount
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I tried ext3 too with the same result.

Here is what looks to me like the relevant part of "dmesg":

```
 [133424.725224] EXT3-fs (sdb): error: can't find ext3 filesystem on dev sdb.
[133424.725319] EXT4-fs (sdb): VFS: Can't find ext4 filesystem
[133424.725388] FAT-fs (sdb): Unrecognized mount option "noload" or missing value
[133598.738011] EXT4-fs (sdb): VFS: Can't find ext4 filesystem
[133736.662950] EXT4-fs (sdb): VFS: Can't find ext4 filesystem
[133903.874913] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem

```

Based on a post I read elsewhere, I ran fdisk and parted to get information that might be useful to someone helping me. Here are the outputs:

```
 leftseat@selous:~/recovered20140605/photorec$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a59df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   226050047   113024000   83  Linux
/dev/sda2       226050048   234438655     4194304   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on a physical sector boundary.

Disk /dev/mapper/cryptswap1: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders, total 8388608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe33a2cd8

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

```
 leftseat@selous:~/recovered20140605/photorec$ sudo parted -l
Model: ATA INTEL SSDMCEAW12 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  116GB  116GB   primary  ext4         boot
 2      116GB   120GB  4295MB  primary


Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  500GB  500GB               primary


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 4295MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4295MB  4295MB  linux-swap(v1)

```

I don't see GPT as a type option in "man mount", and I don't see an option to mount read-only in any of the GUI tools I'm aware of.

Can anyone tell me what I'm doing wrong in trying to mount the hard drive read-only? Should I be using a different file system type?

Thanks very much in advance for your assistance.


Craig

---

### Post by craig10 on 2014-06-07
Figured it out:

```
leftseat@selous:~$ sudo cryptsetup -r luksOpen /dev/sdb1 crypthome
[sudo] password for leftseat: 
Enter passphrase for /dev/sdb1: 
leftseat@selous:~$ sudo mount /dev/mapper/crypthome /romount
mount: block device /dev/mapper/crypthome is write-protected, mounting read-only
leftseat@selous:~$ cd /romount
leftseat@selous:/romount$ touch test
touch: cannot touch ‘test’: Read-only file system
leftseat@selous:/romount$
```

---

