---
title: "I broke edgy; no mouse, network, file systems mounted"
date: 2007-04-13
forum: General Help
---

### Post by Kisil on 2007-04-13
I'm not sure what caused the problem I'm having, but it started when I ran envy to update my nvidia driver.  I had some issues with version incompatibilities between nvidia-core and nvidia-glx, and I ended up turning off the newer nvidia drivers ("nv" instead of "nvidia" in xorg.conf).  At that point I rebooted, and suddenly I was missing my mouse, and network connectivity.  I regenerated xorg.conf, since (I thought) that was the only thing I'd changed, but that made no difference.

It looks to me like I'm not getting all the way through the boot process.  I can't start my network card manually, as eth0 does not seem available, and my non-root file systems are not mounted.  gdm still starts as normal, but with a crippled, mouse-less X server.

Anyone know what I could have done to cause this, how I can debug further, and then how I can solve this?  I could reinstall (I'm writing this from Gentoo on the same machine, so backup is easy), but I'd prefer not to if it can be avoided.  Also I'd like to learn how to fix this sort of thing.


Thanks in advance for any help.

---

