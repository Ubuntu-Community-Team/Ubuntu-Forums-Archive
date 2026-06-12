---
title: "[SOLVED] x server nvidia driver issues"
date: 2007-09-15
forum: General Help
---

### Post by andymushu on 2007-09-15
I recently had the new legacy (9631) drivers set up for my feisty system with a nvidia mx400 and it worked well. Then one day everything decided to stop working (my grub, drivers, mozilla). I fixed everything but this driver issue. Whenever i start up my computer the x server cannot start, and when i try to start it with startx it says that the nvidia API version is 7184, and this session of x is running 9631. if i run the driver installer for 9631 again it works fine, i can startx and everything works normal. however, this is terribly inconvenient, and i was wondering why it would be doing this. i tried uninstalling the drivers completely in envy but the issue prevailed. i thought it was very strange how one day it would just stop working correctly. any help would be much appreciated.

---

### Post by nick_h on 2007-09-16
Did the problems start after a kernel upgrade?  If you installed an nvidia driver from the nvidia site then you will need to re-install it for the updated kernel.

---

### Post by andymushu on 2007-09-16
thank you for the reply. come to think of it, i think i do remember updating my kernel right before all this happened. so how would i go about reinstalling the driver for the new kernel? as i posted before, i have tried to just reinstall the driver, which works only during that session. when i restart my computer it resets back to a different driver. so how do i make the driver changes stay?

update: i reinstalled the drivers using the envy gui and i rebooted and it worked like a charm.

---

### Post by nick_h on 2007-09-16
One thing to check with a driver mismatch is the file */etc/default/linux-restricted-modules-common*. If you have the restricted drivers loaded then you can add "nv" to the disabled modules.

I've never used envy but it seems to make driver installation work for many people.

---

