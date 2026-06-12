---
title: "possible harmful effect of kfind in windows partition"
date: 2007-09-24
forum: General Help
---

### Post by jakartographer on 2007-09-24
I was looking through C:\Windows from Konqueror to answer some of my own questions about WINE, and ended up performing a search with kfind.  I then rebooted, and loaded windows instead of Kubuntu using GRUB.  Windows bluescreened immediately afterwards, and the machine rebooted and pulled GRUB back up.  I'm wondering if kfind stuck a file containing an index of the entire directory somewhere inside C:\WINDOWS (a.k.a. /media/hda2/WINDOWS/ from the Kubuntu perspective), and that windows got all hung up over it, and over-reacted.

1)  Does that sound feasible?  If so, how exactly does kfind index the filesystem?
2)  Does anyone have another idea of what may be wrong?
3)  Does anyone have an idea of how to fix that?  I can't re-install windows (no disk), and wiping the partition and using only Linux isn't a viable option for me (no matter how tempting it may be).

I can give you more information if prompted, but I can tell you right off the bat that the bluescreen lasts only for a fraction of a second before the machine reboots, so I can't get any information from it.

---

### Post by Shazaam on 2007-09-24
Dont know about your error but you might try hitting F8 during the Windows boot to get into safe mode and try a system restore from safe mode.

---

### Post by jakartographer on 2007-09-24
That was the first thing I tried.  The next two things I tried were the other two entries for safe mode.  I got the same effect.

Thanks, anyway.

---

