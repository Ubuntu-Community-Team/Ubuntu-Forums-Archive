---
title: "So is my boot partition ext3 or vfat?"
date: 2006-11-01
forum: General Help
---

### Post by DaveBorealis on 2006-11-01
Hello all,

If i 'sudo fdisk -l'
```

/dev/hda1   *           1        1593    12795741   83  Linux

```
Or if I 'sudo mount'
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
```
My boot partition is ext3, as I partitioned during install.

However, if I 'sudo /lib/udev/vol_id /dev/hda1'
```

ID_FS_TYPE=vfat
ID_FS_VERSION=FAT32

```

Most unexpected.  Anyone know what's up?

I'm running Dapper Desktop.

Best regards,
Dave

---

### Post by louieb on 2006-11-01
What do I know? My sudo mount and sudo fdisk -l are similar to yours. I am runing the Dapper desktop too, but heres my
```
lou@gameu:~$ sudo /lib/udev/vol_id /dev/hda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=8d9ee3d8-bc07-4883-a85a-96729aac718c
ID_FS_LABEL=
ID_FS_LABEL_SAFE=
 
```
How weird? 
If it works I would not worry about it.

---

### Post by DaveBorealis on 2006-11-01
> **louieb said:**
> If it works I would not worry about it.

Ah...but I see it as a challenge.  Besides, to quote Red Green, if it ain't broke, you ain't tryin'!

Dave

(The drive was originally vfat, but as a single partition.  I'm assuming that by divving it up into two it would have had a new filesystem written into it.  Unless I accidentally chose the wrong type, which is a possibility for my absent-mindedly prone brain!)

---

### Post by taurus on 2006-11-01
It has to be ext3 because Linux won't work too well if you install it on a VFAT filesystem!!!

In other words, if it ain't broke, who cares...

---

### Post by DaveBorealis on 2006-11-01
Thanks for the info guys.  And while I am trying to be less of an OS hypochondriac, still I wonder....

---

