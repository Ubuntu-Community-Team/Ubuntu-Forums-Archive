---
title: "reiserfs partition reported as unallocated"
date: 2008-04-07
forum: General Help
---

### Post by mgchan on 2008-04-07
I have an external USB drive which has been attached to a SimpleShare 250gb NAS.  This drive (a 300gb drive) was "claimed" by the NAS - meaning it was formatted to reiserfs.  Now I am having trouble accessing the drive through the NAS (many lock-ups) and would like to access it directly.

However when I attach the drive to ubuntu, and try a 'mount -t reiserfs /dev/sdd /media/storage' it says 'wrong fs type, bad option, bad superblock on /dev/sdd, missing codepage or other error'.  I don't get anything in the syslog.  Gparted reports the drive as "unallocated".  However, when I telnet into my NAS all it takes to mount is essentially that same command - 'mount -t reiserfs /dev/se/4 /share/Storage' where /dev/se/4 is the corresponding device.  It is a busybox system.

I don't have much experience with the reiserfs - is this an issue with having the wrong reiserfs installed, or not having the correct options?

---

