---
title: "**HELP** mdadm array /dev/md0"
date: 2013-01-19
forum: General Help
---

### Post by masterpop on 2013-01-19
Hi,

I was in GPARTED when I accidently hit Delete on /dev/md0 and Applied the changes.

Afterwards, I was unable to mount /dev/md0 because I was getting an error message that said "mount: you must specify the filesystem type"

after some googling it was suggest that I run the following command: sudo make2fs -j /dev/md0

Now I can mount the array, but the data seems to have been lost. Is there anyway to recover the data or is it gone forever?

Any help is hugely appreciated because i have/had *everything* on my RAID.

---

### Post by SaturnusDJ on 2013-01-22
[http://forums.gentoo.org/viewtopic-t-443446-view-previous.html](http://forums.gentoo.org/viewtopic-t-443446-view-previous.html)

Conclusion: Expect it's gone. But with recovery software you might get some stuff back.

---

