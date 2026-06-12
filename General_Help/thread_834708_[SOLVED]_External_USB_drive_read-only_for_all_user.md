---
title: "[SOLVED] External USB drive read-only for all users but root"
date: 2008-06-19
forum: General Help
---

### Post by petzworld999 on 2008-06-19
I have an external USB drive with three partitions on it. Two of them get mounted with full write access for all users. The third, (which is where the bulk of my data is), is read-only for all users but root. Does anybody have any idea why this is happening or how to fix it?

---

### Post by NilsE on 2008-06-19
See if there are entries in your /etc/fstab file for any of them.  All 3 should have the same or similar definitions.  If not, we can go from there.

---

### Post by petzworld999 on 2008-06-19
None of them have entries in /etc/fstab. They always mounted without any entry. Here is my fstab anyway.


```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2 / ext3    defaults,errors=remount-ro 0       0
/dev/hda1 swap swap  pri=42   0       0
# /dev/hda3
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by NilsE on 2008-06-19
Are all 3 formated the same?

---

### Post by petzworld999 on 2008-06-19
All three are formatted as FAT32.

---

### Post by petzworld999 on 2008-06-19
Strange. I just restarted x and all is well. Thank you for your interest and help in my problem.

---

### Post by NilsE on 2008-06-19
> **petzworld999 said:**
> All three are formatted as FAT32.
Using nautilus as root (gksudo nautilus) look at the properties for all 3 mount points and see if you notices what the difference is in the permissions etc. You may be able to change the permissions/owner on the failing one to match the others.

---

### Post by mempman on 2008-06-20
Is there an equivalent /etc/fstab for usb mouted drives?

---

### Post by NilsE on 2008-06-20
> **mempman said:**
> Is there an equivalent /etc/fstab for usb mouted drives?
Not that I am aware of.

Have you tried changing the permissions in Nautilus?

---

