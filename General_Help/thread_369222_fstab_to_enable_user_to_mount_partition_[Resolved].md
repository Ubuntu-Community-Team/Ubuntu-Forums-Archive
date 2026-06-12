---
title: "fstab to enable user to mount partition [Resolved]"
date: 2007-02-24
forum: General Help
---

### Post by undecidable on 2007-02-24
I am having a problem setting up fstab 
to enable a normal user to mount a partition.

My fstab has the lines:
-------------------------------------------------------
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       /docs           ext3    defaults        0       2
/dev/hda9       /home           ext3    defaults        0       2
/dev/hda5       /xfr            vfat    defaults        0       0
/dev/hda6       /D              vfat    user,noauto     0       0
/dev/hda11      none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
-------------------------------------------------------

Everything else works except when I try to mount /dev/hda6 with:
     mount -t vfat /dev/hda6 /D
I get the message:
    "only root can do that"

I can mount /dev/hda6 as root,
I can mount it using system-admin-disks.

If I replace "user,noauto" with "defaults" 
it mounts automatically no problem.

? So what is going wrong with 
     /dev/hda6       /D          vfat    user,noauto     0       0
?

I am using 6.06 Dapper Drake.

thanks for any help.

---

### Post by vayde on 2007-02-24
Try one of these:
 mount /D
 mount /dev/hda6

When you give mount the full syntax with type, device, and mount point you mount it specifically with those parameters, not by going through /etc/fstab hence the 'user' permission specified in /etc/fstab is not being read or used.

The command syntax you used didn't require any entry in /etc/fstab.

Good Luck.

---

### Post by undecidable on 2007-02-24
Vayde in Minneapolis

thankyou!  I had spent 2 hours trying all sorts of combinations, googling etc without luck.

Both:
mount /D
mount /dev/hda6
 work.

---

### Post by undecidable on 2007-02-24
resolved

---

