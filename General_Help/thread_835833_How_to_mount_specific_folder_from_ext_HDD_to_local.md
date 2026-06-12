---
title: "How to mount specific folder from ext HDD to local folder?"
date: 2008-06-20
forum: General Help
---

### Post by bmwman on 2008-06-20
Hello,

I have 3 external HDDs (usb) with 1.5TB data total. I have music, movies, pictures, etc. My goal is to mount the Movies folder on my external drive to the /vars/lib/videos which is the default for MythTV videos? My Ubuntu is on a separate partition.All the hard drives are plugged in directly to the backend PC, they're all NTFS and I know how to do that in windows but not in Linux.

Please help.
Thanks

---

### Post by Happy_Man on 2008-06-20
Quite simple, really (at least theoretically). Open up a terminal (Applications --> Accessories --> Terminal) and enter this: ```
gksudo gedit /etc/fstab
``` When that opens up, do you see how there are entries that look something like this? > # /dev/sda5
UUID=535f538c-bd7d-45f5-8b63-43f3d98e3843 /media/sda5     ext3    defaults    We are going to make our own entry. First, find out what number device your external is registered as (eg, /dev/sda5, /dev/sdc2, etc.). Once you have, go ahead and put something in that looks like this: > /dev/sdc2 <or whatever it is>
 /var/lib/videos     ntfs    defaults,umask=007,gid=46 0 Then reboot, and hope for the best!

---

### Post by bmwman on 2008-06-20
I screwed up :( . I found an "easier" way but I did someting wrong and now I can't mount my drive at all. I right clciked on the drive, then go to the drive tab and there are some settings. You can type in the mount point right there. Now I get some error that's incorrect and can't mount at all.

How to fix that?

P.S. This is what my fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=c87a91b2-8990-4a62-841d-4c55ce241a2e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=23875152-3542-42e2-9815-79f0ecca3c93 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0#

---

### Post by Happy_Man on 2008-06-20
What guide/howto did you follow? What error does it give? 

Try removing "relatime" from the options in /dev/sda4 and see if that helps.

---

