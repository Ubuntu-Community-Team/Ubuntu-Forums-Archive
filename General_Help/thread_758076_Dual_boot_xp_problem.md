---
title: "Dual boot xp problem"
date: 2008-04-17
forum: General Help
---

### Post by steigerwald on 2008-04-17
So the other day I updated to 8.04 beta and now for some reason when I try to load XP, it asks for a disk check, which goes smoothly, then i just get a screen with the default background, and no login interface. what gives?

Tried asking on IRC but no solutions were provided, also I could not find any relevant posts to my problem. Hopefully someone knows whats up. Thanks guys.

---

### Post by forrestcupp on 2008-04-17
I'd say more than likely it was a coincidence and not caused by your update.  If you can't figure it out, maybe try booting to your Windows CD and do a repair installation.  If you do that, you may or may not need to [restore GRUB](http://ubuntuforums.org/showthread.php?t=224351) to be able to get back to Ubuntu.

---

### Post by greenstar on 2008-04-18
You can also boot to the repair console with the WinXP cd and run:
```
fixmbr
fixboot
```

Which should allow you to boot to WinXP (if your WinXP is working).

[More info on WinXP Recovery console.]("http://support.microsoft.com/kb/314058")

After that you'll have to use the live cd to reinstall grub.

HTH,

Greenstar

---

