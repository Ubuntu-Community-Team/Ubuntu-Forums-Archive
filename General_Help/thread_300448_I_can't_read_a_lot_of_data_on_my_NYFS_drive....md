---
title: "I can't read a lot of data on my NYFS drive..."
date: 2006-11-15
forum: General Help
---

### Post by gammyhand on 2006-11-15
I have mounted my NTFS partition but a lot of the folders say they can't read all the information....this is a pain as all my DVD's are backed up on there as I use it as a media streamer and I can only see 14 out of the 34 files that should be in one directory...any ideas? I know the data exists.

---

### Post by taurus on 2006-11-15
How do you mount it in /etc/fstab?

```
cat /etc/fstab
```

---

### Post by gammyhand on 2006-11-15
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=c7f12562-db48-457f-a4a5-993d1de643a1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=BC289197289150EE /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=8dc8a100-f2bf-4e97-b48f-d3a9db745375 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2006-11-15
Why not modify the one for NTFS to look something like

```

UUID=BC289197289150EE /media/hda5 ntfs defaults,nls=utf8,umask=0222 0 0

```

---

### Post by gammyhand on 2006-11-16
I don't know. I don't know enough about it, but I will give it a whirl and see what happens. Can't get any worse :(

---

### Post by gammyhand on 2006-11-16
I have done that and it still can't load most of the stuff in there :(

EDIT: Actually, it took a while to sort itself out but now it works :D

---

