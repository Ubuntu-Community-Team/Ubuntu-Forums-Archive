---
title: "Can't umount devices-Kubuntu"
date: 2006-10-30
forum: General Help
---

### Post by mibadt on 2006-10-30
HI,
I'm on a fresh installed Kubuntu Edgy.
Once I read either a USB disk or a CDROM, I can't umount it afterwards, even after issuing a sync command (as root) and waiting two minutes without any visible (disk light) activity.
Enclosed is a sample from the terminal.

Has anybody a similar experience
 and/or solution?

TIA
---------copy of terminal----------
root@miki-desktop:/media/cdrom# sync
root@miki-desktop:/media/cdrom# umount /media/cdrom
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy

---

### Post by russianpirate on 2006-10-30
Maybe it's used by some program. Run *ps -A* and see what could be using the drive. Also make sure you *cd* out of all the directories on the CD. Try using kde to eject the cd, rather than doing it from console (kde could be using it?)

---

### Post by mibadt on 2006-10-30
Eventually I solved the problem as follows:
After I read the CD's contents and it efused to umount, I opened the CD a second time with Konqueror, closed Konqueror ans Voilla! Afterwards I could umount, and once I entered a second CD it behaved as expected.
;)

---

