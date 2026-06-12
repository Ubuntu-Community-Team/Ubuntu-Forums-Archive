---
title: "Windows kills GRUB?"
date: 2006-12-06
forum: General Help
---

### Post by Kensey on 2006-12-06
I have noticed this on my work box where I have edgy/XP SP2 dual-booting on a SATA drive, but not on my laptop where I have dapper/SP2 dual-booting on an EIDE drive.  Every now and then, the PC will reboot while I'm away and GRUB will turn out to be damaged so that it fails trying to load stage 1.5 or 2 (the error goes by too fast to really see, but it's definitely an error from GRUB so stage 1 at least loads).  Reboot, rinse, repeat.

I would say this happens just about once every two to four weeks.  It *seems* to correlate with Windows Update, but not always.  I ran across a forum post somewhere suggesting it may be related to the Windows Malicious Software Removal Tool.

1) Is this MSRT's fault?
2) If so, can MSRT be told not to mess with my bootloader *ever*?
3) If 2) can't be done, can MSRT be turned off and excluded from future updates?
4) If 2) and 3) are both impossible/irrelevant, can GRUB be installed in such a way that it's no longer affected by whatever MSRT is doing?

---

### Post by rpkehoe on 2006-12-06
I have only heard of this happening with ubuntu and XP on the same HD.  For some reason XP really doesn't like another OS being on the same physical drive, even though it is in a different partition.  But my best suggestion would be to try setting up a seperate /boot partition for stage 2, and hopefully XP will leave it alone.  Might not be the right solution, but it is worth a try.

---

### Post by bulldog on 2006-12-06
I don't think Microsoft has any thing to do with it.
It can't read your Ubuntu partition and the remove tool most likely can not write to the MBR.

So it seems there's another problem going on.

I have certainly one and maybe more screensavers which,when they run,let ubuntu logout.
My screensaver is randomly,so once in a while my ubuntu is logged out,took some time to find out what coursed it though.

---

