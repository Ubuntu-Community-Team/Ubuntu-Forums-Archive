---
title: "Gutsy - keep loosing the &quot;mount&quot; icon for my XP partition"
date: 2008-03-12
forum: General Help
---

### Post by Jethro_uk on 2008-03-12
Hi all,

my system has 4 partitions. 1 main Ubuntu (etx3), 1 linux swap, 1 XP bootable (NTFS), and one "spare" NTFS.

Since installing Ubuntu, it's been quite happy to see and mount the NTFS partitions automatically. I've put the disk mounter applet on my panel, and it's shown 5 disks (floppy, 2 CDROMs and 2 NTFS partitions for unmounting).

Of late, the NTFS partitions have disappeared from the panel, indicating they aren't being mounted.

I know I can manually mount them (although I'm not sure of the *exact* procedure), but I'm more concerned with why this has happened.

The XP system hasn't been booted for ages, sio hasn't had a chance to mark the volume as dirty, which I know can cause mounting problems.

Could anyone advice where to start looking ?

---

### Post by zorlab on 2008-03-12
Had the same issue and found it was because MS had errors or was not shut down correctly.  
I no expert.......
Just a shot.. try booting into Windows,and then reboot to Ubuntu.

---

### Post by Jethro_uk on 2008-03-12
... I could try, but between having the icon, and losing it, I didn't use windows, so how can the disk be marked dirty (unless it's Ubuntu doing it)

---

### Post by Jethro_uk on 2008-03-19
> **zorlab said:**
> Had the same issue and found it was because MS had errors or was not shut down correctly.  
I no expert.......
Just a shot.. try booting into Windows,and then reboot to Ubuntu.

I did this, and - surprise surprise - it worked. However, when I rebooted Ubuntu I'd lost them again. Trying a manual "mount" gave me the message the disks were marked as dirty.

So it seems something in the mount command is setting the disks as dirty, and next boot they disappear.

Is this a bug, or a feature with "mount" ?

---

