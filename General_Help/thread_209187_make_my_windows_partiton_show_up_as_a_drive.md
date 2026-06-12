---
title: "make my windows partiton show up as a drive"
date: 2006-07-04
forum: General Help
---

### Post by Polygon on 2006-07-04
i did a fix in ubuntu 5.10 where i added this line to my /etc/fstab:

```
/dev/hda2 /mnt/windows/ vfat uid=1000,gid=1000,auto,rw,users 0 0
```

and it made a drive appear in the "computer" folder and on my desktop, but since i upgraded to dapper 6.06 i guess it still mounts the partiton, but the only way i can access it is going to /mnt/windows.

is there anyway that i can make it so that my windows fat32 partiton shows up as a drive?

---

### Post by Xhills on 2006-07-04
I think I may know this!

Instead of 

```
/dev/hda2 /mnt/windows/ vfat uid=1000,gid=1000,auto,rw,users 0 0
```

try creating a directory at /media/windows then using this in fstab

```
/dev/hda2 /media/windows/ vfat uid=1000,gid=1000,auto,rw,users 0 0
```

It should now show on the desktop.

Alternatively there are shortcuts...

---

### Post by Polygon on 2006-07-04
but this way it appears in "places" and on the side when im like browsing for files in firefox and stuff. thanks!

---

### Post by Xhills on 2006-07-05
Isn't that what you wanted? The places is a list of all the drives and extra shortcuts stuff that Ubuntu has mounted or you have linked to.

You want it to mount them as drives, but you don't want them to show up?

---

