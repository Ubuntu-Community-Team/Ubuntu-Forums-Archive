---
title: "problems mounting Windows hard disks"
date: 2006-11-10
forum: General Help
---

### Post by stan123 on 2006-11-10
Hey, 
I used to have simple access to my other hard-disk containing Windows 98 files, however now I cannot access it anymore.

When I try to mount it I get the following answer:

mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

Can someone help me mounting hda1 (I got the same problem for 'hda2', though I cannot recall having 2 hard-disks formatted for Windwos...)

[Everything is under K desktop]

Thanks,

Josh.

---

### Post by taurus on 2006-11-10
Open a terminal and paste the output of this command here?

```
sudo fdisk -l
```

---

### Post by stan123 on 2006-11-10
Hey, here is what it says:

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1212     9735358+   c  W95 FAT32 (LBA)
/dev/hda2            1213        2431     9791617+   c  W95 FAT32 (LBA)

Disk /dev/hdc: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2397    19253871   83  Linux
/dev/hdc2            2398        2501      835380    5  Extended
/dev/hdc5            2398        2501      835348+  82  Linux swap / Solaris

What do I do?
Josh.

---

### Post by taurus on 2006-11-10
So you want to mount both /dev/hda1 & /dev/hda2.  Okay, let's do the following.  You need to edit your /etc/fstab to add two entries for those drives.  But of course, always make a backup copy just in case you need to recall the original file again...  Open a terminal and do

```
sudo cp /etc/fstab  /etc/fstab.bak
gksudo gedit /etc/fstab
```
Now, add the following two lines to the end of it.

```

/dev/hda1   /media/first_drive   vfat   defaults,umask=000   0   0
/dev/hda2   /media/second_drive  vfat   defaults,umask=000   0   0

```
Save it and run the next three commands:  create two mount points for both drives, mount them, and check to make sure they are both mounted...

```

sudo mkdir /media/first_drive  /media/second_drive
sudo mount -a
df -h

```
That's all there is.

---

