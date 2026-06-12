---
title: "How do you get rid of GRUB?"
date: 2013-05-05
forum: General Help
---

### Post by Dennistheawesome on 2013-05-05
I am dual booting Windows Xp and Zorin Os. How do you get rid of GNU GRUB? I went into Windows XP Recovery Console and typed in Fixmbr and Fixboot but when i exited to restart GRUB was still there! Can you please tell me how to get rid of it.

---

### Post by The Cog on 2013-05-05
You get rid of it by overwriting it with a different bootloader. I would have thought that fixmbr and fixboot would do that. 
If not, I think that SystemRescueCD (a live cd intended for working on broken systems) has the ability to install its own bootloader code - I've used it in the past to fix a corrupt bootloader.

---

