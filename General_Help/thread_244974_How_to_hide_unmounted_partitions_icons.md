---
title: "How to hide unmounted partitions icons?"
date: 2006-08-27
forum: General Help
---

### Post by yopnono on 2006-08-27
Hi. I dualboot my laptop, Dapper/XP and I like to hide the XP (NTFS) partition icon. Like now I have it unmounted, and still the icon is showed in the Places - Computer section.

Have search high and low on this but... I can't find how to hide the unmounted partition icon.

Anyone?

---

### Post by 505 on 2006-08-27
Just remove the mount from /etc/fstab and they wont show up anywhere. If you remove them you also can't access them of course. Instead of removing them you can also change the mount point (not to /media), and they also won't show up.

---

### Post by yopnono on 2006-08-27
No I have tried that. Is still show the icon.

---

### Post by maka on 2006-08-27
> **yopnono said:**
> No I have tried that. Is still show the icon.

you sure it is unmounted? what happens when you double clikc the partition icon while it is "unmounted"?

---

### Post by szf on 2006-08-27
Rather than remove the lines from /etc/fstab - add the 'noauto' option:

For instance, my linux box has several partitions for Fedora that I don't care to see when I am using Ubuntu:

[FONT="Fixedsys"]
/dev/hdb2       /media/hdb2     ext3    defaults,noauto     0       2
/dev/hdb3       /media/hdb3     reiserfs defaults,noauto    0       2
/dev/hdb5       /media/hdb5     reiserfs defaults,noauto    0       2
[/FONT]

With the 'noauto' option they do not show up on my Desktop upon boot.

---

### Post by taurus on 2006-08-27
Or just mount it somewhere like /mnt/hda3 instead of /media/hda3 in /etc/fstab!!!

---

### Post by maka on 2006-08-27
> **taurus said:**
> Or just mount it somewhere like /mnt/hda3 instead of /media/hda3 in /etc/fstab!!!

actually i just tried this for my extra ext3 partition.  for some reason even when i mount it in the mnt folder, it still appears on the desktop as long as the volumes visible is checked.

---

### Post by yopnono on 2006-08-27
Oh is unmounted all right, If I click on it, I get an error since it's not mounted. 
```
error: device /dev/sda1 is not removable
error: could not execute pmount
```

Have tried MNT aswell, the same. The desktop is not the problem. I've unchecked the desktop icons. I like to hide this partition from "Places - Computer" aswell

Using "noauto" does not help, it's still show the icon for the NTFS partition.
It's like a cdrom it's still have the icon even do it's not mounted.

EDIT: If using noauto and click on it i get an error like, but... still icon.
```
mount: only root can mount /dev/sda1 on /media/ntfs
```

---

