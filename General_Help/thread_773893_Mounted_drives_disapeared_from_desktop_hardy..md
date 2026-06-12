---
title: "Mounted drives disapeared from desktop hardy."
date: 2008-04-29
forum: General Help
---

### Post by caish5 on 2008-04-29
They still appear in places menu.
I installed the ubuntu studio theme and i think it might have caused it, but i'm not sure.
Anyone know where the settings for this are?

Thanks for any help.

---

### Post by Urik on 2008-04-29
When you clicking on them in menu, they should appear on desktop (but why is it done this way - dunno). Hardy does automounting of windows NTFS partitions in a very strange way, not like 7.10. A partitions just absent in /etc/fstab , so it describes them in another place, but where?
Also cannot set permissions on these mounted volumes (on my system it's /media/disk, /media/disk-1    instead of /media/sda1 and /media/sda5 like it was on 7.10).
So, can anyone help us, or give an advice, which manual describes our trouble? (man fstab is not relevant, because these volumes aren't discribed there). Possible gvfsd problems, or our "indirect hands".

---

### Post by ACMiller on 2008-04-29
To caish5: I had something similar after a couple of restarts of hardy and a bit of fiddling (no ubuntu studio though). All my partitions apart from / disappeared, only leaving behind dead links in the places menu and under computer. However, the partitions could still be mounted manually. Turned out the partitions had been completely removed from the fstab file (/.etc/fstab) so I had to manually add them. Might be worth your while to check yours and see if your drives are there. If they aren't there are plenty of good fstabing guides in this forum (and even an automated script somewhere, can't find it now though). See this: [http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab]("http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab")

Hope it helps you.

---

### Post by caish5 on 2008-04-29
Mine are correctly mounted. I just don't have desktop icons.

---

### Post by Hraefn on 2008-04-29
Same issue here - esp. problematic with regards to ejecting the iPod.  Tried to use the unmount command in Amarok, no go, and was used to right-clicking iPod on desktop and selecting eject from there..now, nothing...wonder if it's a bug or needing a personal tweak from me?

Any suggestions would be greatly appreciated.

Thx!
H

---

### Post by caish5 on 2008-05-07
any new ideas here?

---

### Post by c9ops on 2008-05-11
I had the same problem and saw your post.  I installed Ubuntu Tweak and was able to select in the desktop settings to show the icons for mounted drives.  It worked for me... hope it works for you as well.

---

