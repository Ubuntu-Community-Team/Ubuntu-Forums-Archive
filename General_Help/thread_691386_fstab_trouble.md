---
title: "fstab trouble?"
date: 2008-02-08
forum: General Help
---

### Post by MichaëlVD on 2008-02-08
Does this look out of the ordinary to anyone? Something is preventing my computer to shut down or programs to launch after a couple of minutes of use, and I'm trying to find out what it is. Thanks!

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=40abb3ea-34d0-440d-9cee-68963c4b7597 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d8fd67dc-73c7-4638-a587-a483f466746d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/etc/fstab (END)
```

---

### Post by taurus on 2008-02-08
> **MichaëlVD said:**
> Does this look out of the ordinary to anyone? Something is preventing my computer to shut down or programs to launch after a couple of minutes of use, and I'm trying to find out what it is. Thanks!

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=40abb3ea-34d0-440d-9cee-68963c4b7597 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d8fd67dc-73c7-4638-a587-a483f466746d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
**[COLOR="Blue"]/etc/fstab (END)[/COLOR]**
```

You don't actually have that last line in there, do you?

---

### Post by MichaëlVD on 2008-02-08
I guess that last line is not part of the file, but just part of the output of 'less /etc/fstab'.

---

