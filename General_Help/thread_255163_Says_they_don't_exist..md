---
title: "Says they don't exist."
date: 2006-09-11
forum: General Help
---

### Post by Roasted on 2006-09-11
When I go to places-computer, 5 things are listed.

CD ROM 1, CD ROM 2, CDDVD ROM, DVDRW ROM, File System.

I have no idea what CD ROM 1 and CD ROM 2 are. When I double click them, it says they don't exist. Where could they of possibly came from? There's also 2 extra "hard disks" listed in administration-Disks that don't have any known partitions.

Where'd they come from??

---

### Post by monktbd on 2006-09-11
can you copy and paste the results of

> sudo fdisk -l
and
> cat /etc/fstab
into here?

it looks to me like they are being mounted by fstab and maybe again mounted by the gnome-volume-manager.

---

### Post by Roasted on 2006-09-11
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+   5  Extended
/dev/sda2   *          63       30515   244613722+  83  Linux
/dev/sda5               1          62      497952   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+   5  Extended
/dev/sdb2              63       30515   244613722+  83  Linux
/dev/sdb5               1          62      497952   82  Linux swap / Solaris
jason@jason:~$









# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
#/dev/sdb2      /media/sdb2     ext3    defaults,uid=jason      0       0
jason@jason:~$


sda = my main drive.
sdb = my backup drive.
hdc and hdd I have no idea what or why they are there.

I did go into terminal and try unmounting them in the same fashion I would unmount my backup drive, but it said they weren't mounted. *shrug*

---

### Post by monktbd on 2006-09-11
> **Roasted said:**
> 
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


comment the above two lines in your /etc/fstab by putting a # in front.
e.g.
> gksudo gedit /etc/fstab
to edit it.

then the gnome-volume-manager should do the mounting automatically for you when you insert a cd in one of your drives.

some explanation:
hdc and hdd are your cdrom and your dvd drive.
they get mounted as cdrom0 and cdrom1 as you can see above in the fstab listing.

edit: at the end you should do a 
> 
sudo mount -a

to have the changes of the fstab take effect.

---

### Post by Roasted on 2006-09-11
So essentially, Linux mounts my drives twice. You have CDDVDROM and DVDRWROM which are there all the time. Then, when I used the drives, the cdrom0 and cdrom1 get mounted. I noticed that they were mounted after using K3B, which I used both drives for.

---

