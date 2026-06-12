---
title: "Fsck Superblock Problem -- Timely help requested please!"
date: 2007-11-18
forum: General Help
---

### Post by nestcrw on 2007-11-18
I got up today, opened up amarok, and no music from my second disk would show up. When I opened the disk in Nautilus it was like half-mounted. It was really weird. 

I'm really concerned about this since I have about 80 gigs of really well-organized music on there.

So I edited my /etc/fstab to make it check /dev/sdb1 (the disk in question).

/etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=12e9d041-1c0f-4be6-a397-d27708b40cf7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=be616257-c32b-4123-be47-6645473e7c09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1       /media/sdb1     ext3    defaults,errors=remount-ro 0    1

```


When I restarted it tried to run fsck, without success. This is what I get:

 fsck /dev/sdb1
```

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: No such file or directory while trying to open /dev/sdb1

[B]The superblock could not be read or does not describe a correct ext2
filesystem[/B].  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```


I tried running the suggested ```
e2fsck -b 8193 /dev/sdb1
```
and this is what I get:

```
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```


What can I do? I'm pretty good with linux. I've been running ubuntu since 
6.06. I've never really run into anything like this though. 

Any help is greatly appreciated! I have a minimal amount of the music, videos, etc.. backed up!

Thanks!

---

### Post by bingoUV on 2007-11-18
To find the likely location of alternate superblocks, do 
```

sudo umount /dev/sdb1
sudo mke2fs -n /dev/sdb1

```

This will print a list of alternate superblocks that might still be uncorrupted. Try those one by one instead of 8193. Best of luck.

---

### Post by nestcrw on 2007-11-18
Thanks for the quck reply. It's like /dev/sdb1 doesn't exist at all. Was it excluded on boot?

sudo umount /dev/sdb1
```
[sudo] password for john:
umount: /dev/sdb1: not found
```

 sudo mke2fs -n /dev/sdb1
```
Could not stat /dev/sdb1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```

---

### Post by bingoUV on 2007-11-18
```

sudo fdisk -l

```

---

### Post by nestcrw on 2007-11-18
sudo fdisk -l

```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x146d146d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

```

It's only showing the first disk.

---

### Post by bingoUV on 2007-11-18
I think only dealer / service centre can help you now. He will ask you if it works in windows, so try that before taking your hard disk

---

### Post by nestcrw on 2007-11-18
Can windows machines read ext3?

---

### Post by atlfalcons866 on 2007-11-18
> **nestcrw said:**
> Can windows machines read ext3?

yes they can [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by nestcrw on 2007-11-18
Thanks. What about GParted live cd's? Would that help?
Does anyone have experience with those?

---

### Post by nestcrw on 2007-11-18
OK, now I'm really confused, but a good confused.

I took the "1" out of my /etc/fstab, and magically, my disk mounted and everything is there.

I will be backing up everything, reformatting it, and most likely buying a backup hard drive tonight.

Thanks for all of the help.

p.s. If someone could explain why changing 1 to 0 made a difference, that would be great :)

---

