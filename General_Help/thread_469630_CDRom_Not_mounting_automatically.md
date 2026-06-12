---
title: "CDRom Not mounting automatically"
date: 2007-06-10
forum: General Help
---

### Post by xsnslaine on 2007-06-10
When i insert CD's into my CD rom drive ubuntu doesnt mount the CDROM drive, it gives an error saying invalid mount options, yes just mounting manually works no problems

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=406e3a16-43ca-4c5c-801a-b674d3bed171 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b6f66770-5983-4deb-ade3-5079f0194db1 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by viciouslime on 2007-06-10
Which cd drive doesn't work? According to that you have two, is that true?

---

### Post by xsnslaine on 2007-06-10
yes i have 2, both act the same

---

