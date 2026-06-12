---
title: "mounting drive into home folder"
date: 2008-06-22
forum: General Help
---

### Post by jonathonball on 2008-06-22
I have a drive that I would like to mount as part of the home folder.  I would also like the drive to be "transparent" or just appear as part of the filesystem and not be listed as an additional drive in gnome.

the drive is currently mounted as /media/storage, which works yes, but it's not what i want.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=16eba01a-4893-4353-aba9-81e5ba7ad7a9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=a42eaac4-a1fd-4a91-99dd-0b9a3cef64b3 none            swap    sw              0       0
# /dev/scd0 (DVD-RW)
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdc1
UUID=2c373db6-f2ca-4f3d-8c2d-172340d586e5 /media/storage ext3 defaults 0 2
```

any thoughts?

---

### Post by diaa on 2008-06-25
just mount it anywhere other than /media and it'll not appear as an additional drive in gnome.

---

