---
title: "[SOLVED] Mounting Question"
date: 2007-04-05
forum: General Help
---

### Post by Kristopher on 2007-04-05
I have just installed 7.04 dual booting with Vista. On my desktop i have 2 drives mounted

1. HP Recovery
2. sda1 - Vista

When i try to unmount these as I want a clean desktop i get the following

¨Cannot unmount the volume 'HP_RECOVERY'.¨

Details

unmount:/media/sda2 disagrees with the fstab

What does this mean and how do i fix this?

---

### Post by kidders on 2007-04-05
Hi there,

That message seems to suggest you are manually mounting the filesystem somewhere other than the location specified in /etc/fstab, and then trying to unmount it in such a way that the system needs to consult /etc/fstab to find out where it's likely to be.


Try unmounting the filesystem using its /dev alias instead of its mount point (ie **umount /dev/whatever** instead of **umount /media/whatever**).

---

### Post by strabes on 2007-04-06
Post the output of this command: 

cat /etc/fstab

---

### Post by Kristopher on 2007-04-06
Here is the output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=27402da9-a923-4f12-b821-cb9daf3964f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=17D246CA3918226B /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1bf6c206-ff8b-4834-959c-e12b6c05a041 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by kidders on 2007-04-06
> **strabes said:**
> Post the output of this command: 

cat /etc/fstab

The output of **mount** would also be interesting, if you wouldn't mind posting it. Have you by any chance reordered your hard disks recently?

---

### Post by Kristopher on 2007-04-06
Nope the laptop came with C:\ for vista and D: for HP Recovery

Here is the output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=27402da9-a923-4f12-b821-cb9daf3964f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=17D246CA3918226B /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1bf6c206-ff8b-4834-959c-e12b6c05a041 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by kidders on 2007-04-06
Could you post the output of **mount**?

---

### Post by Kristopher on 2007-04-12
Sorry for the late reply but I managed to get it, I commented out the 2 lines on fstab and then in terminal did a sudo unmount and that fixed it. 

I know that completely removed my access to the Vista drives but I have only been on it once since i got my new laptop and installed ubuntu, so it looks like maybe soon ubuntu will be the only OS on my laptop.

Thanks for the help

---

