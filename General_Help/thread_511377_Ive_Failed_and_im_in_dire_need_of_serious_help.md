---
title: "Ive Failed and im in dire need of serious help"
date: 2007-07-27
forum: General Help
---

### Post by Aesir09 on 2007-07-27
i did a partition today, 25gb, for linux, and the program i used asked me the question... are you going to install the OS as soon after this restart? and i clicked yes because i WAS going to


then i decided not too...

but then it kept saying error loading operating system, because my primary HDD is obviously now set to my new partition, hmm so well i used my windows reinstall disC and deleted the partition, but now its just unspecified Gigs of memory.


so now that i did that when i turn my comput on it says strike f1 to retry boot and f2 to enter setup....



I NEED TO SET UP MY PRIMARY HARDDRIVE TO BE THE ONE WITH WINDOWS INSTALLED. EITHER WITH BIOS OR THE CMD TYPE APP IN MY REINSTALL DISC THAT I HAVE BOOTED FROM

---

### Post by Fallen_62 on 2007-07-27
Use your Windows reinstall disk, log into the recovery console, and type these two commands:
```
fixboot
fixmbr
```

See if that helps.

---

