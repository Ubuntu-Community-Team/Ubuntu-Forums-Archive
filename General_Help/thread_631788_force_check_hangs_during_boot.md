---
title: "force check hangs during boot"
date: 2007-12-04
forum: General Help
---

### Post by kefurd06 on 2007-12-04
on boot a friend gets a forced drive check, and it hangs anywhere from 25% to 68% and never ends (no hard drive activity). what do i do?

i've read posts that say to go and disable the check but i can't get to a point in the bash where commands like sudo and fsck are even recognized. help!

---

### Post by Anduu on 2007-12-05
How long has he let it run...I can remember a few times I would have sworn my system was hung but opted to walk away rather than reboot and sure enough I would come back later to see all systems normal.
Depending on the size of the drives and files,what kind of errors need to be fixed etc processes like formatting and disk checking can take a loooong time.
I would leave it run overnight just to be sure.

---

### Post by kefurd06 on 2007-12-05
will do.

---

### Post by kefurd06 on 2007-12-10
well, the guy's vista is hosed. turns out he upgraded to two gigs of ram just a few days before vista crashed. could be bad ram. not sure if the ram was causing a problem with the fscheck; he reinstalled gutsy. we'll find out after about 22 mounts though. :)

btw a ubuntu livecd memory test didn't throw any errors (only ran it once tho)

---

### Post by thoffland on 2007-12-21
You might want to make sure that FSCK isn't trying to scan the Windows HDD/Partition. I had this problem with another (FAT3) drive and it was taking forever to boot. 

Check /etc/fstab and make sure that only your root partition has a "1" at the end... all others should be "0"

ie: 
```
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

This is my laptop so it doesn't show any other drives, but you get the idea.

---

