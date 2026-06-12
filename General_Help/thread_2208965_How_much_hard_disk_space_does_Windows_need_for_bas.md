---
title: "How much hard disk space does Windows need for basic stuph?"
date: 2014-03-03
forum: General Help
---

### Post by t0p on 2014-03-03
I've got a laptop which came with Windows 7.  I did a dual boot, approx half the HD for Win7, the rest for Ubuntu.

I have booted into Win7 three times.  I obviously don't *need* it - but one day I might, you never know, low flying swine and so on.

So: I want to give Ubuntu more disk room.  But I don't know how much disk space I have to keep for Win7 (just for basic stuph, can't see me becoming a gamer or Windows Power User any time soon...).

So: what's the min I can get away with giving to Win7?  Remembering that I hardly ever use it.

---

### Post by westie457 on 2014-03-03
_Warning. Do this while Windows is running_.

If not already done you have to remove the hiberfil.sys file and disable hibernate. This link has advice that worked for me. [http://www.howtogeek.com/howto/15140/what-is-hiberfil.sys-and-how-do-i-delete-it/](http://www.howtogeek.com/howto/15140/what-is-hiberfil.sys-and-how-do-i-delete-it/)

Next open Windows MMC and go to Disk Management. Right-click on the Windows partition and select shrink.
The pop-up window will give the 'minimum size for Windows and the maximum you can shrink by. Not completely sure if Windows decides to allow itself some room for overhead and general usage.

Personally I would be cautious and allow Windows approximately 10% more room than the minimum suggested.

Click Okay/Accept to all screens and then wait for the operation to finish and then reboot to allow Windows to run 'chkdsk' just in case there is any issues.

---

### Post by t0p on 2014-03-03
Thanks, I will try this out later on.

---

