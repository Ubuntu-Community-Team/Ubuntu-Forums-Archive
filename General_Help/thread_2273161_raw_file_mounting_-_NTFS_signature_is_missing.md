---
title: "raw file mounting - NTFS signature is missing"
date: 2015-04-11
forum: General Help
---

### Post by ELMIT on 2015-04-11
I got a backup file from a Jiffybox (Germany), which includes two files, one seems to be the swap partition and the other the root partition.

The README text suggests:

losetup /dev/loop0 name_of_disk_file
mount /dev/loop0 /mnt
... Files are at /mnt ...
umount /mnt
losetup -d /dev/loop0


I tried above:
sudo losetup /dev/loop0 /mnt/data/JiffyBox-Rblog/jiffybox_j12345_disk_87654.raw
sudo losetup /dev/loop1 /mnt/data/JiffyBox-Rblog/jiffybox_j12345_disk_87655.raw

sudo losetup -a
/dev/loop0: [0801]:118489091 (/mnt/data/JiffyBox-Rblog/jiffybox_j12345_disk_87654.raw)
/dev/loop1: [0801]:118489092 (/mnt/data/JiffyBox-Rblog/jiffybox_j12345_disk_87655.raw)

sudo mount /dev/loop0 /mnt/Jiffy-87654
/dev/loop0 looks like swapspace - not mounted
mount: you must specify the filesystem type

sudo mount /dev/loop1 /mnt/Jiffy-87655
NTFS signature is missing.
Failed to mount '/dev/loop1': Invalid argument
The device '/dev/loop1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


dmesg shows:

[139553.362306] EXT4-fs (loop1): VFS: Can't find ext4 filesystem
[145511.175998] EXT4-fs (loop1): VFS: Can't find ext4 filesystem
[145550.608571] EXT4-fs (loop1): VFS: Can't find ext4 filesystem
[145550.608615] EXT4-fs (loop1): VFS: Can't find ext4 filesystem
[145550.608639] EXT4-fs (loop1): VFS: Can't find ext4 filesystem
[145550.608664] FAT-fs (loop1): invalid media value (0x00)
[145550.608665] FAT-fs (loop1): Can't find a valid FAT filesystem
[145550.608789] XFS (loop1): Invalid superblock magic number
[145550.609041] FAT-fs (loop1): invalid media value (0x00)
[145550.609042] FAT-fs (loop1): Can't find a valid FAT filesystem

How can I fix that?

---

