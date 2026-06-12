---
title: "GRUB confused after removing VAIO recovery partition."
date: 2006-12-11
forum: General Help
---

### Post by tscook on 2006-12-11
Sony threw Windows XP and their evil 7GB "recovery partition" back on after they repaired my laptop, so I decided to set it up to dual boot XP and Xubuntu (since I love Xs so much).  However, I think I did things in the wrong order; setting up Xubuntu and Grub before removing the  recovery partition.  Booting back up, Grub still pointed to the recovery partition and I suppose it is looking for XP in the wrong place. How do I get Grub to catch up

---

### Post by bernied on 2006-12-11
Have a look at this thread, see if there's enough there to sort you out
[http://www.ubuntuforums.org/showthread.php?t=314027](http://www.ubuntuforums.org/showthread.php?t=314027)

---

### Post by tscook on 2006-12-11
That link shows essentially one of the methods I tried, but the part that I had not seen yet was menu.lst

hda2 would be read as hd0 by GRUB, right, since even though it is named as two it is in reality the first?

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *           1        3017    24234021    7  HPFS/NTFS
/dev/hda3            3018        9544    52428127+  83  Linux
/dev/hda4            9545        9729     1486012+   f  W95 Ext'd (LBA)
/dev/hda5            9545        9729     1485981   82  Linux swap / Solaris

```

But then, the GRUB menu should have only hda2 as hd0 as opposed to (hda1 was previously the recovery partition):

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

So couldn't I just edit this? Is that an option in the GRUB shell?

It is most likely that I am reading the other thread wrong, but it seems to be addressing a different problem?  Hopefully this will be more helpful to those who can help a newbie.

---

### Post by bernied on 2006-12-11
Have I misunderstood? Is it just Windows that doesn't boot?

If that is the case, then editing the menu.lst file might fix it. That second entry should do the job. Have you tried that?

What did you do to delete the recovery partition?

---

