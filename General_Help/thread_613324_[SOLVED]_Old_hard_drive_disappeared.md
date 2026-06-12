---
title: "[SOLVED] Old hard drive disappeared"
date: 2007-11-14
forum: General Help
---

### Post by niprat on 2007-11-14
I installed Ubuntu on a new HD and it recognized my old XP HD, added it to the Ubuntu desktop and mounted it in the media folder.  

I rebooted and used XP for a day or so and now Ubuntu won't find that old drive anymore, what changed? and how do I get it back?

---

### Post by jfernyhough on 2007-11-14
Last time this happened to me was when I reformatted one of my NTFS drives and it changed the UID. I had to delete the old mount point in /media (> sudo rm -R /media/mount), and the easiest way to get it back was to run ntfs-config (which may need aptitude install-ing first). Pick a mount point for the drive (deleting the old one means you can reuse it, otherwise it errors), and say OK. Bingo, it's back.

---

### Post by niprat on 2007-11-14
Thanks, when I installed that NTFS-Config app it told me that I needed to shut down windows properly (instead of hard reset), once I did that everything was back to normal.

Thanks again.

---

