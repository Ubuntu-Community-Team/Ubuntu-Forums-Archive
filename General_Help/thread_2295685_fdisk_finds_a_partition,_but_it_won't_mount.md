---
title: "fdisk finds a partition, but it won't mount"
date: 2015-09-20
forum: General Help
---

### Post by BlackTornado on 2015-09-20
Hello.

I have a Debian server on a plug pc with attached an external "combo" USB/eSata enclosure with a lot of data in.

I had to reinstall Debian on the server (the system is on sd card, and it gets easily corrupted) and I am now trying to attach the external enclosure.

Unfortunately, I don't seem to be able to do it: if I connect the enclosure through eSata, nothing happens: nothing in dmesg, and nothing appears in fdisk either.

If I instead connect the enclosure through USB, I can see it with fdisk, but I cannot mount it:

```
Device         Boot  Start      End  Sectors  Size Id Type
/dev/mmcblk0p1 *      2048   499711   497664  243M 83 Linux
/dev/mmcblk0p2      499712 31115263 30615552 14.6G 83 Linux

Disk /dev/sda: 746.5 GiB, 801569726464 bytes, 1565565872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors Size Id Type
/dev/sda1           1 4294967295 4294967295   2T ee GPT

```

Trying to mount it, I get this (I tried different version of the command, with or without specifying the partition type, trying with both /dev/sda and /dev/sda1

```
daniele@sheevaplug:~$ sudo mount /dev/sda1 /home/daniele/esata/
mount: special device /dev/sda1 does not exist
daniele@sheevaplug:~$ sudo mount /dev/sda /home/daniele/esata/
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
daniele@sheevaplug:~$ sudo mount -t ext4 /dev/sda /home/daniele/esata/
[ 6971.903263] EXT4-fs (sda): VFS: Can't find ext4 filesystem
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
daniele@sheevaplug:~$
daniele@sheevaplug:~$ sudo mount -t ext4 /dev/sda1 /home/daniele/esata/
mount: special device /dev/sda1 does not exist

```

Any idea what I am doing wrong?

---

