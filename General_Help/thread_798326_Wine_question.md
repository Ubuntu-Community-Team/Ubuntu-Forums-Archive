---
title: "Wine question"
date: 2008-05-18
forum: General Help
---

### Post by Iztari on 2008-05-18
I have a dual boot with Ubuntu and XP in my laptop, and I was wondering if there is any way to map the real windows folder (from my XP partition) to wine. I'm just curious because I think that would make wine a little more stable. Or maybe mapped the real C:/ to wine.

Edit:
I was also wondering how the library tab in the wineconfig works.


-Thanks

---

### Post by Iztari on 2008-05-28
bump

---

### Post by prshah on 2008-05-29
> **Iztari said:**
> I have a dual boot with Ubuntu and XP in my laptop, and I was wondering if there is any way to map the real windows folder (from my XP partition) to wine. 

If you map your Win XP partition to Wine's C: drive, that's a surefire way to disaster. WINE has it's own binaries that are used as "replacements" to Windows binaries; that means that it will replace your actual Windows files with it's own.

So when you next try to boot into windows, the files will be unrecognized (since they are unix binaries).

In short: don't do it.

If you want to persist (in the valley of death, rode the six hundred...) you can map your c: drive to your WinXP partition using the winconfig program (Usually Applications-Wine-Configure Wine-Drives). (Cannon to the right of them, cannon to the left of them, volleyed and thundered...)

---

