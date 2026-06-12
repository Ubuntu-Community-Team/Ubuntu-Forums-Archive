---
title: "lsblk shows incorrect UUID after reformatting a LVM logical volume"
date: 2017-03-24
forum: General Help
---

### Post by Paddy Landau on 2017-03-24
I have noticed a bit of a problem with lsblk.

If I query the UUID of a LVM logical volume (partition), with lsblk or blkid, they correctly show me the UUID.

Now, I reformat the logical volume, and again query. blkd correctly shows the new ID, but lsblk incorrectly shows the old UUID. This is repeatable, again and again, even if I change the file system.

Here is my test LVM partition.
```
[COLOR=#000080]$ sudo lvscan[/COLOR]
  ACTIVE            '/dev/sample/lvsample' [5.00 GiB] inherit
```
I create a file system, in this case a swap. Notice the UUID. When I query with lsblk or blkid, they show it correctly.
```
[COLOR=#000080]$ sudo mkswap --label=swap /dev/mapper/sample-lvsample[/COLOR]Setting up swapspace version 1, size = 5 GiB (5364510720 bytes)
LABEL=swap, UUID=**e282aa46-d795-4a58-ae3f-22493eae8520**


[COLOR=#000080]$ lsblk --fs --paths /dev/mapper/sample-lvsample[/COLOR]
NAME                        FSTYPE LABEL UUID                                 MOUNTPOINT
/dev/mapper/sample-lvsample swap   swap  **e282aa46-d795-4a58-ae3f-22493eae8520**


[COLOR=#000080]$ sudo blkid /dev/mapper/sample-lvsample[/COLOR]
/dev/mapper/sample-lvsample: LABEL="swap" UUID="**e282aa46-d795-4a58-ae3f-22493eae8520**" TYPE="swap"
```
I redo this, but using ext4 this time. Notice what happens: the UUID changes, blkid correctly shows this, yet lsblk still shows the old UUID.
```
[COLOR=#000080]$ sudo mkfs.ext4 -L data /dev/mapper/sample-lvsample[/COLOR]mke2fs 1.42.13 (17-May-2015)
/dev/mapper/sample-lvsample contains a swap file system labelled 'swap'
Proceed anyway? (y,n) [COLOR=#000080]y[/COLOR]
Creating filesystem with 1309696 4k blocks and 327680 inodes
Filesystem UUID: **939e5277-ad72-4c83-af8f-00ccd9e5a1ae**
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736


Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done 


[COLOR=#000080]$ lsblk --fs --paths /dev/mapper/sample-lvsample[/COLOR]
NAME                        FSTYPE LABEL UUID                                 MOUNTPOINT
/dev/mapper/sample-lvsample ext4   swap  **e282aa46-d795-4a58-ae3f-22493eae8520**


[COLOR=#000080]$ sudo blkid /dev/mapper/sample-lvsample[/COLOR]
/dev/mapper/sample-lvsample: LABEL="data" UUID="**939e5277-ad72-4c83-af8f-00ccd9e5a1ae**" TYPE="ext4"
```
Is this something that I should report as a bug? If so, where, as it doesn't look like an Ubuntu-specific fault?

---

