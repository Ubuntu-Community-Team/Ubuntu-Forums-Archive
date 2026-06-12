---
title: "unable to mount windows partitions"
date: 2007-02-09
forum: General Help
---

### Post by mrpeenut24 on 2007-02-09
My computer has the following partitions:
sda1:  WinXP System, 8GB
sda2:  General Storage, XP program, document directories, 45GB
sda3:  WinVista, 21.5GB
(all primary)

And up until recently had Ubuntu on another primary partition.  However, I recently decided to put a swap disk on it so I could hibernate (I have 2GB RAM, so I'm not sure why I would need this, but I did)(also whenever I try to hibernate now, it just shuts down...), and now it's not allowing me to mount my Windows partitions.  When I installed Ubuntu the first time, it gave me an option of where to mount each one, but the last time it didn't.  I edited my fstab file to this:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3f3f120d-a4dc-4491-ac3f-078952f5c346 /               reiserfs notail          0       1
# /dev/sda6
UUID=4130d0c8-c597-4237-af8e-8c63d35d2e23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# edited to automount Windows partitions
/dev/sda1    /media/windows    ntfs    umask=0222    0    0
/dev/sda2    /media/storage    ntfs    umask=0222    0    0
/dev/sda3    /media/vista    ntfs    umask=0222    0    0
and it mounts the drives, but I'm unable to open them.  I imagine it's a problem in the options, but I'm not sure how to change it.
I downloaded mountpy, and it mounted them as ro, which is better than nothing (I would prefer rw), but I would ideally like to have them config'd in fstab to mount at startup, and I would like the 'Computer' folder &/or Desktop show them mounted as disks (it only mounts them as folders in /media/ when using mountpy).

Any help?  Also any idea about the hibernate issue?

---

### Post by Graydonhicks on 2007-02-09
I am having trouble with my windows partition also.  The windows (xp) mounted, but I am only able to see .mdm and .msm files, along with a "dell" folder that only has some opening screen pictures.  The partition editor sees the hda1 partition, but it only shows to be using 6gb of the 20gb available,...and I know that my windows partition takes up more than that.  The file extensions (in the partition editor) show several kinds,....ext1, fat16, fat32, and so on.

---

### Post by LPomfrey on 2007-02-09
Have you tried using ntfs-3g? A lot of people say they have problems with it but when I used it with a Win partition it worked spectacularly.

---

### Post by mrpeenut24 on 2007-02-09
Will this allow it to load on boot?  This is really what I'm trying to do, and if possible, I'd rather edit the fstab config.

---

### Post by Entity` on 2007-02-09
I too want to mount NTFS drives so i can access them and read/write to them
the starter guide doesnt seem to help.

---

