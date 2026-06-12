---
title: "Trying to restore vista but is grub stopping me?"
date: 2008-01-17
forum: General Help
---

### Post by adamgibbo on 2008-01-17
i want to restore vista i also have gutsy but when i use the acer eRecovery in vista it asks me for my password then restarts. Im sure then after it reboots the recovery is supposed to start but grub boots and its a normal start. is grub stopping the eRecovery from starting? if so how can i stop it stoping it?
Im sure somebody must know.
Thank you for your help.

---

### Post by DrMega on 2008-01-17
Your recovery tool will be setting a flag in Windows to tell it to continue on boot, but Grub is stopping you from getting that far. You just need to choose Windows at the boot menu and it will carry on as normal.

---

### Post by adamgibbo on 2008-01-17
No this is not working vista just starts as normal. Is the "flag" suppose to start before vista starts to boot? This is why i thought that grub might be starting rather than the "flag" and if so how do i disable grub so it doesn't stop it?:confused:

---

### Post by DillyP on 2008-01-17
Try pressing Alt+F10 when it boots up- that is supposed to make it boot into eRecovery.  If that doesn't work, maybe editing grub to point to that partition.

---

