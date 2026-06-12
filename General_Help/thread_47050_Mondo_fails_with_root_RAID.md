---
title: "Mondo fails with root RAID"
date: 2005-07-07
forum: General Help
---

### Post by sjpwong on 2005-07-07
I have setup a server with RAID1 for both the root partition and the swap partition.

I wanted to take an image of the machine so that I can restore it if required so I used mondoarchive from universe.

I've used it plenty of times and have found it to be excellent on non RAID systems.

What I have found is that when I boot from the CD created by mondo (Ubuntu kernel and failsafe kernel) it fails stating that it cannot mount /dev/md0 (my root RAID1 device)?

I have searched around a lot and found some references to needing raidtools under Fedora Core.

Raidtools is not in Ubuntu Hoary.

Does anyone have a work around for this?

Should I install that package from Debian?  Would it even help?

---

