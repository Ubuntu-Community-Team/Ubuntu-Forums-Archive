---
title: "Mount Second Hard Drive"
date: 2006-12-04
forum: General Help
---

### Post by ART_Adventures on 2006-12-04
Hello People,

I have two hard disks. The second one is a single FAT32 partition. It shows up in the Gnome Partition editor as /dev/sdb/.

I would like to mount this drive, and I would ideally like it to mount automatically each time I start Ubuntu so I can access this drive when needed. Can anybody help me do this?

Thanks.

---

### Post by Jimmey on 2006-12-04
Create a folder to mount it to like so:
> sudo mkdir /media/sdb/

Then you want to edit FSTAB. Do it like this:
> gksudo gedit /etc/fstab 

Then you want to make the device /dev/sdb1 mount to /media/sdb with type fat32 and options default. I think if you start a new line, and type
> /dev/sdb1[TAB]/media/sdb/[TAB]fat32[TAB]defaults

Note that the "fat32" option might be wrong, I'm not at an Ubuntu machine right now :-P

---

### Post by taurus on 2006-12-04
> **Jimmey said:**
> Create a folder to mount it to like so:


Then you want to edit FSTAB. Do it like this:


Then you want to make the device /dev/sdb1 mount to /media/sdb with type fat32 and options default. I think if you start a new line, and type


Note that the "fat32" option might be wrong, I'm not at an Ubuntu machine right now :-P

```
/dev/sdb1   /media/sdb   vfat   defaults,umask=000   0   0
```

---

