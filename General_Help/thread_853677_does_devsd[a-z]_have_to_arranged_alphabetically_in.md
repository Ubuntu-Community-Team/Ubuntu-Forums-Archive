---
title: "does /dev/sd[a-z] have to arranged alphabetically in fstab"
date: 2008-07-08
forum: General Help
---

### Post by mempman on 2008-07-08
I wanted to know if /dev/sd[a-z] drives in /etc/fstab have to be mounted alphabetically.  I have 2 different /etc/fstab files, and the first file works but causes massive problems when I'm trying to burn cds:


First file that causes massive problems: 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=956ba4c7-12a2-40d5-8351-cf2b48d09355 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3E97-07BC  /STORE          vfat    utf8,umask=002,gid=46 0       1
# /dev/sda2
UUID=59c57080-a859-49cb-bdfd-2988b7129f6f /home           ext3    relatime        0       2
# /dev/sda5
UUID=950c47ed-152a-4d98-9e61-b40848b7f95d none            swap    sw              0       0
[B]/dev/scd0       /media/cdrom0	auto   users,noauto,exec,utf8 0       0
/dev/sda1	/STORE3		auto	utf8,umask=002,gid=46	0	1[/B]

```


Second file, that doesn't cause any problems:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=956ba4c7-12a2-40d5-8351-cf2b48d09355 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3E97-07BC  /STORE          vfat    utf8,umask=002,gid=46 0       1
# /dev/sda2
UUID=59c57080-a859-49cb-bdfd-2988b7129f6f /home           ext3    relatime        0       2
# /dev/sda5
UUID=950c47ed-152a-4d98-9e61-b40848b7f95d none            swap    sw              0       0
**/dev/scd0       /media/cdrom0	auto   users,noauto,exec,utf8 0       0**

```

---

### Post by sdennie on 2008-07-08
Alphabetical order shouldn't make any difference, no.

---

### Post by Victormd on 2008-07-08
the problem isn't in the order, but your very last column on the last line of the first file (confusing... hehehe) should be 0, not 1 since fsck can't/shouldn't check partitions other than ext2 or ext3. Furthermore, your root filesystem is the only fstab entry that should have a 1, other ext2/3 partitions can have a 2.

In your case, you have a fat partition with a 1 as well and should be set to 0.

---

### Post by mempman on 2008-07-08
> **Victormd said:**
> the problem isn't in the order, but your very last column on the last line of the first file (confusing... hehehe) should be 0, not 1 since fsck can't/shouldn't check partitions other than ext2 or ext3. Furthermore, your root filesystem is the only fstab entry that should have a 1, other ext2/3 partitions can have a 2.

In your case, you have a fat partition with a 1 as well and should be set to 0.

How can you tell that /STORE3 is fat filesystem.  Although it actually if fat32, the fstab entry simply states "auto."  So how did you know that it was fat32?

Also, I thought that fsck can be run on ex2/3fs, and it can be run on msdos as well.  Doesn't fsck automatically use fsck.msdos.

---

### Post by VMC on 2008-07-09
> **mempman said:**
> How can you tell that /STORE3 is fat filesystem.  Although it actually if fat32, the fstab entry simply states "auto."  So how did you know that it was fat32?
Because it says so:
UUID=3E97-07BC  /STORE          [COLOR="Red"]vfat[/COLOR]    utf8,umask=002,gid=46 0       1

---

### Post by mempman on 2008-07-09
> **VMC said:**
> Because it says so:
UUID=3E97-07BC  /STORE          [COLOR="Red"]vfat[/COLOR]    utf8,umask=002,gid=46 0       1

I was actually referring to /STORE3.  My understanding is that the fsck option for / should be 1.  All other partitions, including fat and ntfs paritions, should have their fsck options set to '2.'

Please do correct me if I am wrong.

---

### Post by Victormd on 2008-07-09
> **mempman said:**
> I was actually referring to /STORE3.  My understanding is that the fsck option for / should be 1.  All other partitions, including fat and ntfs paritions, should have their fsck options set to '2.'

Please do correct me if I am wrong.

I didn't know what the file system was for /STORE3 but assumed it was FAT because you used the same options as /STORE (i.e., utf8,umask=002,gid=46	0	1)

For "/" it should be 1, that's right, but from what I understand, it can't/doesn't handle NTFS (not to sure about FAT/FAT32 but would think it's the same) and that's why I suggested you change it to 0 instead of 2. That simply means that fsck will ignore checking the file system on those partitions. Also, my suggestion is that it should be set to 2 only on ext2 or ext3 partitions. On that note, you have /STORE and /STORE3 fsck set to 1 and that should only be set as 1 for "/".

---

