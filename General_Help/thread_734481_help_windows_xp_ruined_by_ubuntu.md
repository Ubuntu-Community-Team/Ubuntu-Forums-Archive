---
title: "help windows xp ruined by ubuntu"
date: 2008-03-24
forum: General Help
---

### Post by juliopjuliop on 2008-03-24
help i currently installed ubuntu today im pretty new to ubuntu ive used it for about 6 months. well i installed it on a lapto and i had 2 xp installations but 1 didnt work so i formated the second xp partition and now i got the ntldr missing so i fixed it by manually coppyinge the files back to the first partition but now i install linux and the partition is in ext3 and i dont know were to install the ntldr.com etc and now to top it off grub was deleted by my xp cd so i can no longer use ubuntu and i have no mbr neither xp mbr or grub my xp and linux instalations are intact and i have no problem reinstalling linux but first i nee to install the xp boot mbr can some1 help? any ideas or suggestions would be apreciated.:(:(:confused:

---

### Post by pieisgood4589 on 2008-03-24
> **juliopjuliop said:**
> help i currently installed ubuntu today im pretty new to ubuntu ive used it for about 6 months. well i installed it on a lapto and i had 2 xp installations but 1 didnt work so i formated the second xp partition and now i got the ntldr missing so i fixed it by manually coppyinge the files back to the first partition but now i install linux and the partition is in ext3 and i dont know were to install the ntldr.com etc and now to top it off grub was deleted by my xp cd so i can no longer use ubuntu and i have no mbr neither xp mbr or grub my xp and linux instalations are intact and i have no problem reinstalling linux but first i nee to install the xp boot mbr can some1 help? any ideas or suggestions would be apreciated.:(:(:confused:

Pop in the XP install CD, but instead of selecting Install, select Fix/rescue, or whatever the option is. Then, in the DOS prompt, just type in "fix mbr"

---

### Post by juliopjuliop on 2008-03-24
> **pieisgood4589 said:**
> Pop in the XP install CD, but instead of selecting Install, select Fix/rescue, or whatever the option is. Then, in the DOS prompt, just type in "fix mbr"

well you see ive tried taht but when i get to there it does not show my current installation of windows xp it just shows it as partition 3 and when i click ener on it it shows no repair selection were you press r for repair it just shows what way i want to format it so i cancel.

well on another note i have thought up a plan i will make a very small (5gigs partition for just a plain xp install). then i will just add the line too the boot.ini off my old xp installation and keep the 5gig installation of xp for when i may have this problem again what do you guys think?

---

