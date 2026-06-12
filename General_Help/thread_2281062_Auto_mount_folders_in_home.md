---
title: "Auto mount folders in home"
date: 2015-06-04
forum: General Help
---

### Post by dagring on 2015-06-04
Hi,

I have a problem of mounting shares from another hard disk in in my home folder. I have my music and videos on an other hard drive, and I want it these files to appear under Music and Videos in the home folder. The Videos works nice, but the music just directs me to the hard disk, and it is not possible to acess other shares on this disk. My fstab is like this:

  GNU nano 2.2.6                                        Fil: /etc/fstab                                                                                      

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=1c163458-46d8-4455-bd8a-093d12922cbd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fe515055-fb2f-4adf-b042-fac23d16ae05 none            swap    sw              0       0
UUID=25019a70-1441-46dc-af5a-822545927f78 /media/storagea ext4 defaults,noatime 0 2
/media/storagea/Videoklipp /home/dag/Videoklipp auto bind 0 0
/media/storagea/Musikk /home/dag/Musikk auto bind 0 0


Can anybody give me a hint on how to put this right?

Dag R

---

### Post by Keith_Helms on 2015-06-04
Shouldn't the bind entries in fstab contain the word none instead of auto?

---

### Post by dagring on 2015-06-04
I tested this after you sent me the answer, but it does not make any difference.

---

