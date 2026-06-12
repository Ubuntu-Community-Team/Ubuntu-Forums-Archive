---
title: "Replacing a computer with ubunto"
date: 2013-07-16
forum: General Help
---

### Post by Spokechuck on 2013-07-16
My low powered atom box just died.  If I buy a cheap computer, can I just swap in the hard drive and expect ubunto to boot up, or is it more complicated?

thanks,

cr

---

### Post by TheFu on 2013-07-16
It will probably work, but your eth0 will be reserved and an eth1 will probably be created. You can leave it alone or manually clean up the udev directory if you like.

I've moved HDDs between systems many times. The only time it failed to work was when I accidentally moved to an incompatible processor (64-bit to 32-bit) or when other hardware like RAID controllers didn't exist in the newer system, but the boot process expected them.  If you aren't doing any of that - go ahead. Only the ethernet devices will be different.  Ah - if you have proprietary GPU drivers and swtich to a different GPU, that could be an issue too. I would expect the driver to recognize that the GPU it expects is not there, then load the default FLOSS driver instead, but I've never tried it.

---

### Post by 3rdalbum on 2013-07-16
Yes, it should boot up. If you had Nvidia or ATI graphics on the first computer it might be a different story, but with an Intel Atom system you should be fine.

---

### Post by GerryB on 2013-07-17
Excellent previous comments. I've done it many times without any problems. Your old atom box might just need a new power supply if your hard drive still works.

---

