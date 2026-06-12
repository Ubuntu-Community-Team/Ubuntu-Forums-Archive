---
title: "Problems mounting FAT32 partition (Solved)"
date: 2006-10-10
forum: General Help
---

### Post by chejrw on 2006-10-10
Hey everyone. I'm sure the solution to this is simple, it's just not coming to me.

I just installed Dapper, and I set it up with 4 partitions on my hard drive - a large NTFS with XP on it, then an EXT3 partition for Ubuntu, a small swap, and then the rest of my space (~15GB) I made into a FAT32 patition so that I can mount it read/write in linux and use it to share files between the two OS's.  Makes sense, right?

Anyway, windows assigned it drive letter D and is fine with it, but I can't mount it in Ubuntu.  The NTFS partition mounted fine (read only, of course), but when I try to mount the FAT32 drive, I get the errors:

```
error: device /dev/hda2 is not removable
error: could not execute pmount
```

The partitions were set up with gparted from a live session, if that matters.

Any help?  The whole point of this FAT32 partition is so that I can read and write files from it in both OS's.  If Linux can't mount it, it doesn't really help me.

---

### Post by taurus on 2006-10-10
What is the ouput of this command from a terminal, Applications -> Accessories -> Terminal?

```
sudo fdisk -l
```

---

### Post by aysiu on 2006-10-10
These instructions should help you mount it properly:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by cap_gemo on 2006-10-10
1. Install ntfs-3g and you can also write to NTFS.
  2. To discover the problem with your FAT32 partition do following:
    a. Run as suggested "sudo fdisk -l" and check, if your FAT32 partition is really hda2.
    b. Run sudo "nano /etc/fstab" and check the line, corresponding to your FAT32-partition. It must look like something like this:

/dev/hda2  /windows/d  vfat  defaults,utf8,umask=007,gid=46 0       1

(assuming your mount point is /windows/d)

    c. After you'vde done corrections to /etc/fstab, run the following commands:

    sudo umount -a
    sudo mount -a

  If after that your FAT32-Partition doesn't work, I don't know what to do...

---

### Post by chejrw on 2006-10-10
sudo fdisk -l outputs the following:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7178    57657253+   7  HPFS/NTFS
/dev/hda2            7179        8453    10241437+   b  W95 FAT32
/dev/hda3            9696        9729      273105    5  Extended
/dev/hda4            8454        9695     9976365   83  Linux
/dev/hda5            9696        9729      273073+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

nano /etc/fstab brings up this:  As you can see, the FAT partition does not appear.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

EDIT:  one other thing:  I added 
/dev/hda2       /fatfiles       vfat    iocharset=utf8,umask=007,gid=46 0 1
to fstab, but when I tried unmounting (sudo umount -a) I get the following errors:
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy


Any help?

---

### Post by taurus on 2006-10-10
Okay.  Now, what is the output of this command from a terminal then?

```
df -h
```

---

### Post by chejrw on 2006-10-10
I get

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4             9.4G  2.5G  6.5G  28% /
varrun                506M   76K  506M   1% /var/run
udev                  506M  168K  506M   1% /dev
/dev/hda2             9.8G  702M  9.1G   8% /fatfiles
/dev/hda1              55G   48G  7.8G  86% /media/hda1

```

I manually mounted it to /fatfiles but it still isn't showing up anywhere.

---

### Post by randell6564 on 2006-10-10
> **chejrw said:**
> Solaris
[/code]
nano /etc/fstab brings up this:  As you can see, the FAT partition does not appear.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

EDIT:  one other thing:  I added 
/dev/hda2       /fatfiles       vfat    iocharset=utf8,umask=007,gid=46 0 1
to fstab, but when I tried unmounting (sudo umount -a) I get the following errors:
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy


Any help?

First, the "fat partition" did not appear because you did not add it to you /etc/fstab yet.  
Second, Why would you "**sudo umount -a**" AFTER adding /dev/hda2 to your fstab?! You want to '**sudo umount -a**' FIRST, THEN add /dev/hda2, save it and THEN do a '**sudo mount /dev/hda2**'

---

### Post by taurus on 2006-10-10
What do you mean it doesn't show up everywhere?  Well, it shows up in "df -h"!!!  Try adding this line to your /etc/fstab and reboot!

```

/dev/hda2   /fatfiles   vfat   defaults,umask=0000   0   0

```

---

### Post by randell6564 on 2006-10-10
> **taurus said:**
> What do you mean it doesn't show up everywhere?  Well, it shows up in "df -h"!!!  Try adding this line to your /etc/fstab and reboot!

```

/dev/hda2   /fatfiles   vfat   defaults,umask=0000   0   0

```
EXACTLY! THEN do a '**sudo mount -a**'

---

### Post by chejrw on 2006-10-11
Thanks guys.  That worked.  I also set the mount point to /media/fatfiles so that it shows up on the desktop.

Thanks for all the help.

---

### Post by taurus on 2006-10-11
Whatever mounts in /media will show up on your desktop.

---

