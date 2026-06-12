---
title: "pmount broken in Edgy?"
date: 2006-10-27
forum: General Help
---

### Post by fordy on 2006-10-27
In Dapper I had three devices listed in pmount.  These were fat32 partitions on the same drive as Ubuntu.  Having upgraded to Edgy, the pmount file still contains the correct entries, but I cannot mount the partitions - They no longer appear in the "Computer" window and if I try to use my old short cuts, Edgy tries to mount them as floppies.  Where is the Disk Manager?  At least I used to be able to use that. :evil: 

If I can't get this sorted, my next question will be, how do I revert to Dapper?

---

### Post by marcozs on 2006-10-27
post your /etc/fstab ...

---

### Post by fordy on 2006-10-27
Here is fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda10 -- converted during upgrade to edgy
UUID=7e38890b-4024-4b11-a3e3-3145e94c03c3 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda11 -- converted during upgrade to edgy
UUID=27c4ddf6-d2ce-438d-aa42-c0f797afe6a7 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


And here is pmount.alow:
# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
/dev/hda5
/dev/hda6
/dev/hda7

hda5, hda6 and hda7 are the partitions I need to mount, but they no longer appear in the "Computer" list.

---

### Post by fordy on 2006-10-27
OK.  I sort of fixed this.  I have the three partitions now mounting through "fstab" and have removed the entries from pmount.allow.

What I think had happened is that the folders in the "media" directory had, somehow, got their names converted to uppercase during the upgrade.  This meant that the shortcuts I had on the desktop didn't work and the pmount icons were not present in the "Computer".  Couple that with there being no Disk Manager which allowed me to specify mount points and, BAM! no disk partitions.

This sort of change needs better testing and documentation before release IMHO.

---

