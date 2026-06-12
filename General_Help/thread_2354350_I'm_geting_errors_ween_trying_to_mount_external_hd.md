---
title: "I'm geting errors ween trying to mount external hdd"
date: 2017-03-02
forum: General Help
---

### Post by orbitmipi on 2017-03-02
I get this popup error:

```
Error mounting /dev/sdb1 at /media/odroid/ext4_backup: Command-line `mount -t "ext4" -o
 "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/odroid/ext4_backup"' exited with non-zero exit
 status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


```

I dont know if this erelavint but It hapend after using and instaling ext2explore-2.2.71 on windows.

EDIT: Well now wen I plug in the mybook in to windows pc it says I need to format to read. Also the ntfs the ubuntu can read is now empty. :( but the propertys say it has data  on the pi pikter but abuve it it says free space unknown and contens: nothing.
my hdd is 2gb etx4 and 1 gb ntsf.

EDIT: well I fixd the ntsf by chkdsk g:/f on windows

---

### Post by ajgreeny on 2017-03-02
Plug in the external drive and with it unmounted, which it sounds as if it will be, run ```
sudo e2fsck /dev/sdb1
``` to see what errors, if any, Ubuntu can find in that partition.

I used an ext driver in Windows XP a very long time ago, just to be able to read and copy files from my Ubuntu partition back to Windows, but I have no idea what it was as it is now too long ago, but I never had any problems of this sort with it.

I wonder if UEFI is involved, if you are booting in UEFI mode and have GPT partitions?

---

### Post by orbitmipi on 2017-03-11
sry 4 the delay.

I dont know much about UEFI. The HDD was partitiond with Gparted.

```


root@odroid:/home/odroid# e2fsck /dev/sdb1e2fsck 1.42.13 (17-May-2015)
ext2fs_check_desc: Corrupt group descriptor: bad block for block bitmap
e2fsck: Group descriptors look bad... trying backup blocks...
ext4_backup was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 40108187 has out of order extents
    (invalid logical block 20480, physical block 8421376, len 32768)
Clear<y>? 
ext4_backup: e2fsck canceled.


ext4_backup: ***** FILE SYSTEM WAS MODIFIED *****

```


I pusher ctrl+c to atempt copy the code but it thout I was ansering the question 

```

Clear<y>?

```

EDIT: It seems most of the files on that partition ar back. Now I just have to go thru it manualy and see what files need replaced. But I can mount again without having to format :)

---

