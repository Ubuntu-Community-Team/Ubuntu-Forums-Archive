---
title: "Grub problem"
date: 2006-12-31
forum: General Help
---

### Post by neolite on 2006-12-31
So i've had Ubuntu installed for a while with xp pro n the same HD, and decided to get another HD just for Ubuntu, s i deleted the partitions it made and that seem to work fine. but now i can't access windows at all. computer fires up then GRUB starts t lad and comes up with an Error: 22. and won't go any further. IS there anyway i can srt this withut having t wipe the entire HD and reinstalling everything?

---

### Post by ajgreeny on 2006-12-31
You need to reinstall the windows MBR using your windowsXP install CD.  If you have a CD that reinstates software that came on your machine originally, rather than a windowsXP CD you may have a problem and have to get a rescue disk to boot the computer and fix the MBR.

Search *fixmbr* on google and you will find masses of info to answer your question, but basically, startyour comp with the winXP cd in the drive and the machine set to boot from CD.  When the system has loaded go to the recovery suite and look for *"fixmbr".*  That should do it.

---

