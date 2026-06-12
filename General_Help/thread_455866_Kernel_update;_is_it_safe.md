---
title: "Kernel update; is it safe ?"
date: 2007-05-27
forum: General Help
---

### Post by Wim Sturkenboom on 2007-05-27
This morning I found a kernel update for Dapper. However, Synaptic tells me that it was NOT authenticated. I downloaded it, but did not install it as I did not trust it.

linux-image-2.6.15-28-386; extended info says linux-image-2.6.15-28-53 will be upgraded to linux-image-2.6.15-28-55

Is it safe to install?
If so, how do I install the downloaded version?

---

### Post by hardyn on 2007-05-27
it probably is... but there is always a certain about of risk with such a core update.

the best policy is to sit back for a couple of days, and check this forum to see if there are any complaints about the new kernel.

cheers.

---

### Post by Wim Sturkenboom on 2007-05-27
:D

I was wondering why it's NOT authenticated. As far as I can remember, the other kernel updates were authenticated.

---

### Post by hardyn on 2007-05-27
i cant answer that with any certainty... but it may have a back-ported component, back-ports do not get authenticated.

---

### Post by Wim Sturkenboom on 2007-05-28
Anybody else an opinion why the update is not authenticated?

---

### Post by Steve- on 2007-05-28
Well, I got no such error for the Kernel update for 7.04 and that was most definitely not safe, since Ubuntu won't boot anymore.

---

### Post by allwin on 2007-05-28
Yeah, it's "safe" ymmv.  I updated an old system with an ATI card using open drivers and Beryl, went just fine.  Updated a newer system with an old nVidia card and Beryl.  Had to rerun ENVY to reinstall the nVidia driver.  THEN THE FUN BEGAN...my hard drive, which used to be /dev/hda, changed to /dev/sda.  I had to update (with Feisty) stuff like hdparm.conf and fstab for my windows partitions.  Well, now this kernel update changed things back to /dev/hda once again.  BONUS...I can set the 32 bit mode and DMA and all that good stuff now!!!  Unfortunately I had to redo all the other tweaks made to /dev/sda.  Grumble.

---

### Post by ferd on 2007-05-28
I'm running dapper on an old system with KDE and upgraded with no problems. My system seems to be more responsive after the upgrade.

---

### Post by Noremacam on 2007-05-28
If you got it as "unauthenticated" you better make sure it came from an ubuntu repository instead of another custom repository you may have installed.

---

### Post by Wim Sturkenboom on 2007-05-29
@Noremacam:
and how do I do that?

---

