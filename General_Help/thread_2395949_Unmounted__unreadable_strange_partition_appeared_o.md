---
title: "Unmounted / unreadable strange partition appeared on disk"
date: 2018-07-09
forum: General Help
---

### Post by leopheard on 2018-07-09
Hi all,

When I installed Lubuntu back in 2014, I'm fairly sure it created three partitions - a FAT32 boot, main data in EXT4 and a swap file of sorts.

I've noticed that a 7.89 GB (entire drive is 500GB) partition has appeared when I use gparted, and it shows unmounted and unable to detect the filesystem.

I don't believe it's my encrypted home folder/subfolders, as there's more than 7GB in there (well over 15GB I think). Any ideas?

Can I just reformat this partition as a swap file under EXT4? Will the system being to use it normally?

EDIT: fschk says the following:

[COLOR=#000000]fsck from util-linux 2.27.1[/COLOR]
[COLOR=#000000]e2fsck 1.43.1 (08-Jun-2016)[/COLOR]
[COLOR=#000000]ext2fs_open2: Bad magic number in super-block[/COLOR]
[COLOR=#000000]fsck.ext2: Superblock invalid, trying backup blocks...[/COLOR]
[COLOR=#000000]fsck.ext2: Bad magic number in super-block while trying to open /dev/sda3[/COLOR]


[COLOR=#000000]The superblock could not be read or does not describe a valid ext2/ext3/ext4[/COLOR]
[COLOR=#000000]filesystem. If the device is valid and it really contains an ext2/ext3/ext4[/COLOR]
[COLOR=#000000]filesystem (and not swap or ufs or something else), then the superblock[/COLOR]
[COLOR=#000000]is corrupt, and you might try running e2fsck with an alternate superblock:[/COLOR]
[COLOR=#000000]e2fsck -b 8193 <device>[/COLOR]
[COLOR=#000000]or[/COLOR]
[COLOR=#000000]e2fsck -b 32768 <device>[/COLOR]

---

### Post by HermanAB on 2018-07-09
Linux cannot boot of a FAT partition, so things are not as you remember.

---

### Post by leopheard on 2018-07-18
The FAT32 partition has a boot flag, but not sure if that means it's the mount point or what.

Either way, can I delete the erroneous partition and resize my main partition to make use of that data?

---

