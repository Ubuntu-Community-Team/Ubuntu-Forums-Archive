---
title: "tune2fs/ext2-&gt;ext3 bug??"
date: 2008-01-07
forum: General Help
---

### Post by malibu on 2008-01-07
Today I found out that I mistakenly formatted an external USB drive and a non-root internal partition to ext2 instead of ext3.  I wasn't too upset because I knew I could do the convert and I an unmount them both on the running system so it shouldn't be too hard..

Well this evening I ran the tune2fs -j and changed the /etc/fstab to indicate ext3 on the external partition (it's a two-LV filesystem).  It mounted find and df -T shows it as an ext3.  Great.

But now when I reboot, it fails and gives me an error message about the superblock not correctly indicating that it's an ext2!!  If I take the partition out of the fstab at that point the boot finishes and I can then mount the drive manually as ext3.

Does anyone know what is causing this?  I'm afraid to try my internal drive because it has more important data on it.

Thanks!

---

### Post by dcstar on 2008-01-08
> **malibu said:**
> Today I found out that I mistakenly formatted an external USB drive and a non-root internal partition to ext2 instead of ext3.  I wasn't too upset because I knew I could do the convert and I an unmount them both on the running system so it shouldn't be too hard..

Well this evening I ran the tune2fs -j and changed the /etc/fstab to indicate ext3 on the external partition (it's a two-LV filesystem).  It mounted find and df -T shows it as an ext3.  Great.

But now when I reboot, it fails and gives me an error message about the superblock not correctly indicating that it's an ext2!!  If I take the partition out of the fstab at that point the boot finishes and I can then mount the drive manually as ext3.

Does anyone know what is causing this?  I'm afraid to try my internal drive because it has more important data on it.

Thanks!

I would guess that your LVM settings (somewhere) need changing?

---

### Post by malibu on 2008-01-08
Right you are.. I knew about this before.. but suddenly it dawned on me that it might be the cause of the problem.  Originally I had two windows partitions and one Linux partition on the disk and had carved it up with Partition Magic.  The Linux partition somehow got a 'FAT16' type but it worked fine so I hadn't thought anything of it.  Anyway I changed it to LVM as it should be and the problem still seems better but I'm still having one..  

I'm going to post another thread about it..  Now having my external USB drive partitions in /etc/fstab doesn't interrupt the boot process... But they don't mount either.  Can't figure out what it is.

---

