---
title: "I just erased the contents of my &quot;media&quot; folder"
date: 2007-09-10
forum: General Help
---

### Post by mjpatey on 2007-09-10
I can't believe I did this...

I just formatted a new external USB hard drive as FAT32 using gparted, and did the following in a terminal:

```
sudo fdisk -l
```

(which showed that my newly formatted drive came up as "sda1"), then...

```
sudo mount /dev/sda1 /media
```

GASP!  That mapped my new drive to the media folder, but rather than adding the drive to my drives in the folder, it replaced *everything* in it with just the mount for my new hard drive!

So what I'm trying to do is mount the new hard drive, and at this point, get back all the partitions and physical drives that I just stupidly deleted the references to!  Is there an easy way to do this?

[-o<

---

### Post by ryno519 on 2007-09-10
> **mjpatey said:**
> I can't believe I did this...

I just formatted a new external USB hard drive as FAT32 using gparted, and did the following in a terminal:

```
sudo fdisk -l
```

(which showed that my newly formatted drive came up as "sda1"), then...

```
sudo mount /dev/sda1 /media
```

GASP!  That mapped my new drive to the media folder, but rather than adding the drive to my drives in the folder, it replaced *everything* in it with just the mount for my new hard drive!

So what I'm trying to do is mount the new hard drive, and at this point, get back all the partitions and physical drives that I just stupidly deleted the references to!  Is there an easy way to do this?

[-o<

sudo umount /media

?

Try unmounting it and see if everything is still there afterwards.

---

### Post by jocko on 2007-09-10
Check the contents of your /etc/fstab:
```
cat /etc/fstab
```
Check for all references to mountpoints under /media/
Recreate them by:
```
sudo mkdir /media/"foldername"
```
and add a new folder to mount your new disk with the same command.
To have your new disk mounted automatically on boot:
```
gksudo gedit /etc/fstab
```
And add a new line like this (if the partition is ext3 formatted):
```
/dev/sda1 /media/"newfolder"    ext3    defaults        0       2
```
And to mount everything:```

sudo mount -a
```

---

### Post by mjpatey on 2007-09-10
Thanks to both of you!  I tried the first suggestion (from ryno) and that did indeed restore my original list of drives at their original mount points.  The second suggestion (from jocko) worked like a charm, too, and now my drive is appearing right where I want it.

\\:D/

Thank you!!!

-Mark

---

