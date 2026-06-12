---
title: "Problem while starting Ubuntu"
date: 2008-02-28
forum: General Help
---

### Post by nemodot on 2008-02-28
I have a problem while starting ubuntu. The Ubuntu logo is loading, then switchs off and shows me a list of the process that are loading. First, it check file systems.

But when it does than with my FAT32 partition (SDA 5), takes long time checking and later show this:

```
* Checking file systems...
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32 LFN
There are differences between boot sector and its buckup.
Differences: (offset:original/backup)
  28:3f/ef, 29:00/40, 30:00/08, 31:00:07
  Not automatically fixing this.
/dev/sda5:  208524 files, 2470461/4798998 clusters
```

I had logged in on windows and run a scandisk. But the problem remains.

Ubuntu starts later, but it bothers me beacause it takes too much time checking that partition.

PD: sorry for my englishhhhh...

---

### Post by taurus on 2008-02-28
It is not a good idea to run fsck for ntfs and/or fat partitions.  

Open a terminal and post your /etc/fstab.

```
cat /etc/fstab
```

---

### Post by nemodot on 2008-02-28
This came up:

```
esteban@esteban-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=3c34e00b-3a4a-47b8-8320-36dfee3eb5e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5ABCF3B3BCF38831 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=44EB-73F7  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=f4debdee-3b1f-4d5f-bb89-c98866e35382 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by taurus on 2008-02-28
I would change the last digit for ntfs and vfat entries from 1 to 0.

```

# /dev/sda1
UUID=5ABCF3B3BCF38831 /media/sda1     ntfs    defaults,umask=007,gid=46 0       [COLOR="Blue"]**0**[/COLOR]
# /dev/sda5
UUID=44EB-73F7  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0      **[COLOR="Blue"] 0[/COLOR]**

```

---

### Post by nemodot on 2008-02-28
What would that do?

---

### Post by taurus on 2008-02-28
It would stop the kernel from scanning both of your ntfs and vfat partitions.  But if you don't want to change them from 1 to 0, then don't.

---

