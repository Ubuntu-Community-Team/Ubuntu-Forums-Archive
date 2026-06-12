---
title: "Accessing Hard Drive Causes Lock Up"
date: 2008-06-12
forum: General Help
---

### Post by dmar on 2008-06-12
I am having problems accessing an internal hard drive on Ubuntu 8.04. Whenever I try to mount it, fsck it, or access it in any way the computer will lock up hard. (The hard drive activity light stays lit on the PC, and the mouse and keyboard do nothing.) The only way to reboot it is to hold down the power button on the PC. I have tried checking the system logs to see if they show anything unusual, but it all seems rather normal to me. I have tried to see if the live CD would give me a different result, but it is still the same. I have tried it on the newest version of SLAX, and it was able to access the drive without locking up. I also tried the live CD from Ubuntu 7.04, and it worked fine as well. I fsck'ed it and it gave back no errors.

It is formatted with EXT3. It used to be NTFS, but I noticed it kept locking up and thought it might be the NTFS driver. I copied my necessary data off it and reformatted it using SLAX because anytime it went to access the drive in Hardy it would lock up.

Is there anything that you can think of that might be wrong?

Thank you!

---

### Post by Titan8990 on 2008-06-12
IMO this sounds like a hardware issue. I would check you DMA settings in your BIOS. Is this a SATA or IDE drive?

---

