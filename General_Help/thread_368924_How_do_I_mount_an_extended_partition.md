---
title: "How do I mount an extended partition??"
date: 2007-02-23
forum: General Help
---

### Post by billdotson on 2007-02-23
I just created an extended partition that contains a 25GB FAT32 partition and a 10GB XFS partition.
I also have a 225GB NTFS partition (not extended) that I want to mount.

I created it using gparted from the Ubuntu Edgy Eft LiveCD.  Do I need to format these drives or did gparted already format them?  

What do I put in my /etc/fstab to automatically mount the xfs, fat32 and ntfs partitions on boot-up?

here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c51e7206-7183-4cee-b79f-142eb72cbc1b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=1e0d2ef5-41dc-4288-8518-4814ecc5c585 none            swap    sw              0       0
/dev/hda        /media/dvd   udf,iso9660 user,noauto     0       0
/dev/scd0        /media/dvdrecorder   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1    /media/Windows_ntfs ntfs  nls=utf8,umask=0222 0    0
/dev/sdb4    /media/Backup_ntfs ntfs  nls=utf8,umask=0222 0    0

The /dev/sdb4 at the bottom is the ntfs partition and I think I mounted it right but I have no idea what to do with the xfs (/dev/sdb5) and fat32 (/dev/sdb6)

---

### Post by llamakc on 2007-02-23
Wasn't this related?

[http://ubuntuforums.org/showthread.php?t=368888](http://ubuntuforums.org/showthread.php?t=368888)

Have you researched the "mount" command yet?

An xfs partition is just mounted similar to an ext3 one, but with "xfs" as the <type>.

You edit your /etc/fstab and add them.

---

### Post by billdotson on 2007-02-23
yes that was related but I would just like that one discontinued. 

So do I have to format/reformat the partitions to be able to use them?

what do I put in the /etc/fstab for my fat32, ntfs and xfs partitions?

I think these lines are how to get the ntfs and the fat32 to mount:

/dev/sdb4    /media/Backup_ntfs ntfs  nls=utf8,umask=0222 0    0
/dev/sdb6   /media/FAT32   vfat   iocharset=utf8,umask=000   0   0

but I do not know how to do the xfs partition.

I just need to be able to get these mounted.  Once I know the umask stuff and other stuff that goes after the filesystem I would suppose I would know how.  I assume the stuff that comes after the filesystem name is the same for each filesystem.  I know how to mount filesystems but not how to put them in the fstab.

---

### Post by Kateikyoushi on 2007-02-23
Follow these steps to mount the fat partition. [LINK]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")
Try this for xfs.

```
sudo mkdir /media/xfs
sudo mount -t xfs /dev/sdb5 /media/xfs
```

---

### Post by billdotson on 2007-02-24
yes thank you.  that does mount it but what I want it to do is to have it in the /etc/fstab so that it automatically mounts on boot-up

---

### Post by billdotson on 2007-02-24
so let me clarify.. I do not have to format these partitions as gparted has already done that?

---

### Post by yabbadabbadont on 2007-02-24
/dev/sdb5 /media/xfs xfs default 0 1

---

### Post by Kateikyoushi on 2007-02-24
I just wanted to try if that mounts the partition correctly before adding it to your fstab, what I always do before adding parititions to my fstab.

```
/dev/sdb5 /media/xfs xfs rw
```
This will remount your fstab without reboot.
```
sudo mount -a
```

---

### Post by billdotson on 2007-02-24
So do I have to format/re-format before I can use these partitions?

---

### Post by JohnPhys on 2007-02-24
GParted should have asked you if you wanted to format the partitions, so it might have.  I don't know if it can format ntfs, though, as I'm not sure if that depends on being able to write ntfs files.

---

### Post by llamakc on 2007-02-24
> **billdotson said:**
> So do I have to format/re-format before I can use these partitions?

No, you do not need to format them unless you want to format them. Is there data on them already that you want access to?

---

