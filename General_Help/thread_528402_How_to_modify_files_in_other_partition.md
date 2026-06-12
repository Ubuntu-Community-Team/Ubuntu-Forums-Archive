---
title: "How to modify files in other partition?"
date: 2007-08-17
forum: General Help
---

### Post by agent407 on 2007-08-17
How do I make it so i can modify files on my windows xp partition? I want to use ubuntu as a backup os so i can backup windows so i can easily restore if a catastrophe occurs. What do i need to modify in this file, fstab, to be able to modify ntsf files?

  GNU nano 2.0.2              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde4
UUID=7f7f4f2b-8b60-4fd5-b8b9-1162fe5c6e69 /               ext3    defaults,erro$
# /dev/sde1
UUID=946C09BB6C09995E /media/sde1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/sde2
UUID=423B-2BDF  /media/sde2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sde3
UUID=b50d662f-dbda-4f2f-850e-0f21b00c0052 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by merlinus on 2007-08-17
```

sudo apt-get install ntfs-config

```

then

```

sudo ntfs-config

```

Tick appropriate boxes and restart.

-merlin

---

### Post by Blindraven on 2007-08-17
please post the output of your /etc/fstab

---

### Post by agent407 on 2007-08-17
fstab is in my first post.

---

### Post by merlinus on 2007-08-17
Did you install and run ntfs-config?  If so, /etc/fstab has changed, so post it again.

-merlin

---

### Post by agent407 on 2007-08-17
Ok i did that, i reeboted, windows xp needed to scan c for errors, it fixed them, and now i am downloading something so i will reply with fstab tommorow, thanks for help.

---

