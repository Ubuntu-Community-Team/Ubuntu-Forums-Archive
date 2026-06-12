---
title: "Change Ownership of Folders and Files External USB Drive"
date: 2018-09-04
forum: General Help
---

### Post by Chris_Nicol on 2018-09-04
I have an external USB drive attached to a Ubuntu 16.04 LTS Sever.  I am backing up some data to the drive using rsync.  I have done this many times before, but the difference this time is the drive is formatted exFAT.  Below is the results of fdisk -l:

```

Disk /dev/sdc: 3.7 TiB, 4000787029504 bytes, 7814037167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: B8B4B235-41EE-4A86-B6D3-A7D30D97CACE

Device      Start        End    Sectors  Size Type
/dev/sdc1      34     262177     262144  128M Microsoft reserved
/dev/sdc2  264192 7814035455 7813771264  3.7T Microsoft basic data

```

I have not had any trouble in the past changing permissions, but if I mount this drive it will not let me change the permissions.  I get "Operation not Permitted"

Chris

---

### Post by Holger_Gehrke on 2018-09-04
exFAT is still FAT and FAT can't store ownership (or Unix-style permissions or POSIX ACLs or ...)

Holger

---

### Post by oldfred on 2018-09-04
Windows formats do not support Linux style ownership & permissions.
The only setting you then have is the default you have when you mount the partition.

Generally using Windows formats for Linux backup is not recommended as you lose all the individual file & folder ownership & settings permissions.
If just user data, you can reset to defaults, but you will never recover correct settings for any system folders or files.

---

### Post by ajgreeny on 2018-09-04
I believe you can add all that you want to backup to an archive, eg tar.gz which will retain all permissions in the contained files.
This is great in theory but managing and restoring single files from that archive will be a great deal more difficult.

---

