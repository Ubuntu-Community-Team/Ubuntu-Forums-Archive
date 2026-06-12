---
title: "disappearing partitions"
date: 2007-09-29
forum: General Help
---

### Post by AuToFiRE on 2007-09-29
Hello, I have not modified any of the system files and yet when i got home late last night and wanted to listen to some music while finishing up some work and the drive i keep it all onwas locked and i wasnt allowed in and i checked properties and the data used was 0 bytes even though there i used over 58 gigs on it, this was my ntfs partition of 100 gigs, and since i keep my computer on pretty much 24/7 i am not sure how it could have disappeared like that, anyone know how to recover it and everything on it?

---

### Post by dcstar on 2007-09-29
> **AuToFiRE said:**
> Hello, I have not modified any of the system files and yet when i got home late last night and wanted to listen to some music while finishing up some work and the drive i keep it all onwas locked and i wasnt allowed in and i checked properties and the data used was 0 bytes even though there i used over 58 gigs on it, this was my ntfs partition of 100 gigs, and since i keep my computer on pretty much 24/7 i am not sure how it could have disappeared like that, anyone know how to recover it and everything on it?

Reboot and unmount the drive, then do a fsck on it.

---

### Post by AuToFiRE on 2007-09-30
I couldnt unmount it since it was apparently already unmounted, and then i rebooted and it doesnt see it at all nowso i ran fsck and it doesnt see it either, only sda1

```

omega@omegaaf:~$ fsck /dev/sda2
fsck 1.40-WIP (14-Nov-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2

```

so from what i see it is still recognizing the partition, its just not being seen since it knows its ntfs

And thank you very much for the help so far since i am new and very glad i have switched to linux so far and the community is so kind in helping an advanced geek in windows gain his ground in linux too

---

### Post by Sef on 2007-09-30
Get [GParted]("http://gparted.sourceforge.net") which has a check disk option.   It may fix your problem.   It also has Test Disk which may or may not be able to diagnose or fix the problem.

---

