---
title: "Boot splash works, shutdown doesn't?"
date: 2007-11-21
forum: General Help
---

### Post by Culito on 2007-11-21
Usin' the Edgy - older comp with onboard AGP video.

I messed around for a while and got my boot splash working with Startup Manager.  It finally started working when I changed the resolution to 800x600.  The kernel line reads VGA=771.  My monitor's native resolution is 1280x1024, but the current settings are the only ones that work...the splash looks fine.

I still don't have a splash screen on shutdown, though!  It just goes to black with a cursor in the upper left corner, then the power shuts off.  Is there different settings for the startup and shutdown splashes?

Thanks,
-C

---

### Post by mpierce on 2007-11-21
You didn't say what type of graphics card your old computer has, i.e., nVidia or ATI, etc.

If it is nVidia, get the package, nvidia-xconfig, install and launch it to configure your video card. There are other programs that can do similar things I'm not familiar with ATI cards.

Hope this helps...

---

### Post by Culito on 2007-11-26
My graphics adapter is this:

Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)

Is there a choice of drivers for this?

---

