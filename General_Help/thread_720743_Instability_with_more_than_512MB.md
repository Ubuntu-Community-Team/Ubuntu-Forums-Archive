---
title: "Instability with more than 512MB"
date: 2008-03-10
forum: General Help
---

### Post by mikelygee on 2008-03-10
I recently upgraded the memory on my laptop (HP Pavilion ZE 4300, ATI radeon graphics, 2.2 GHz Celeron) from 512 MB to 768 MB. It was running Ubuntu 7.10 reliably before then (with a custom kernel, to add "TuxOnIce" for suspending). After the upgrade, the system has become much less stable, crashing unpredictably, and often refusing to start or "wake" from hibernation.

I seem to remember reading somewhere about a known bug caused by a developer mis-reading a spec, and hard-coding a 512 MB limit in his code. Of course, now I can't find anything about this. Does it ring a bell with anyone out there? Any other ideas why a memory upgrade would make a system less stable?

---

### Post by walsh416 on 2008-03-10
Just a guess, but have you tried specifically installing it in Ubuntu somehow?:confused:

---

### Post by oldos2er on 2008-03-10
Run memtest on your new memory. It should be one of the boot options in grub.

---

