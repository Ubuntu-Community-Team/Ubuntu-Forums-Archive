---
title: "Fstab file, UUID lines"
date: 2007-03-19
forum: General Help
---

### Post by SBFC on 2007-03-19
I have a quick question about my fstab file, which is pasted below.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=be2d2932-6f76-48f1-9442-6238de20c49b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=fec3ccd5-49c9-4808-891b-321c914f6f2f /boot           ext3    defaults        0       2
/dev/mapper/main-home /home           ext3    defaults        0       2
# /dev/sda8
UUID=f969644a-9552-40b5-a196-afeefdf88132 /opt            ext3    defaults        0       2
# /dev/sda7
UUID=4feae194-5a9b-4bf2-9459-cc93cb55bc58 /tmp            ext3    defaults        0       2
# /dev/sda9
UUID=887b892d-ab55-4b38-abaf-871dbc018c53 /usr            ext3    defaults        0       2
# /dev/sda10
UUID=beb147a7-de29-4d61-9899-b867dbe0180b /usr/local      ext3    defaults        0       2
/dev/mapper/main-var /var            ext3    defaults        0       2
# /dev/sda6
UUID=dc312af5-4380-49b4-85b4-d54754d1b587 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

When I was using Debian the fstab file never had any lines beginning with UUID. Why are the /dev lines commented out and replaced with the UUID lines? Makes it a lil confusing to look at.

---

### Post by CocoAUS on 2007-03-19
I'm not sure why they made the change, but you certainly don't need the UUIDs there--the device path works just dandy.  Perhaps searching for a bug report or changelog will surface an explanation?

UPDATE:

Apparently using (relative) device paths can cause problems when the device is removed or changes location, or when a device fails to initialize properly.  Because UUIDs are absolute per device, they are not affected by any relative changes.

For more, see:
[http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/sysadmin-guide/ch-devlabel.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/sysadmin-guide/ch-devlabel.html)

---

### Post by Jorge on 2007-03-21
sda  numbers are sequential, so if you "insert" a new partition before a system one (root or swap) the hole system gets confused or won't start. UUID are unique identifiers, no matter which sequence the partitions follow.

---

### Post by qpieus on 2007-03-21
yes, this was an intentional change (with edgy) for the reasons listed by CocoAUS and Jorge.

---

