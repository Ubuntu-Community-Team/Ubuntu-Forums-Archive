---
title: "LILO Bootloader startup time ~2min until bios data check is successful"
date: 2014-11-30
forum: General Help
---

### Post by toogley on 2014-11-30
Hello,

i have installed a minimal Ubuntu installation on my Thinkpad T520 with LILO as bootloader (forgot to remove grub before)
Anyway, the lilo boot process from "linux loaded" to "bios data check successful"  takes up to 2 min. The "delay" entry in /etc/lilo.conf made no difference. 

So, how can i reduce the startup time? Or would it make more sense to install grub2?
And i would like to know, why lilo needs so much time to load.

Thanks.

PS: The Ubuntu community is very lovely :3

---

### Post by tgalati4 on 2014-11-30
Yes, install GRUB2, LILO was designed for much older hardware using a different bootstrap kernel.  It's possible that the LILO bootstrap has problems with your motherboard and has to wait for hardware detection that doesn't happen correctly.  GRUB2 should work out-of-the-box.

---

### Post by toogley on 2014-11-30
Thanks, i will try that then. :)

EDIT: Thanks also for the welcome greeting^^

---

### Post by tgalati4 on 2014-11-30
Oh, and welcome to the community.

---

