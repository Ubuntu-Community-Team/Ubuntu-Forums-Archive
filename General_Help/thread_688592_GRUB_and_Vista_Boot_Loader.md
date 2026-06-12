---
title: "GRUB and Vista Boot Loader"
date: 2008-02-05
forum: General Help
---

### Post by Harvp on 2008-02-05
I have 3 HDDs. 

- 250GB that is all XP (C:)
- 300GB that is half Ubuntu 7.10 and half Vista(E: and F:)
- 40GB holding music and the boot partition for Ubuntu (D:)

When I boot I get to GRUB. Ubuntu launches fine however the boot option for Windows XP, before Vista launched XP, now launches the Vista boot menu. From their I can launch Vista or XP.

All of that is working. 

What I want to be able to do is boot from any of the OSs from GRUB. Also if I choose Vista I don't want a boot menu. (The second request here is something I think I can do on my own just throwing it in there)

How would I be able to do this?

---

### Post by logos34 on 2008-02-05
What you've described is normal--vista takes over the bootloader for both OS's, so when you choose either in grub you still get the vista screen where you can then choose XP or vista.  

To be able to boot XP separately without going through the vista boot menu I think you would have to run **fixboot** from the XP install CD recovery console on the XP partition, then delete XP entry from vista boot manager.  Oh, and then reinstall the vista bootloader on the vista partition (because it automatically installs on the 'active' partition--i.e. the XP partition.)

---

