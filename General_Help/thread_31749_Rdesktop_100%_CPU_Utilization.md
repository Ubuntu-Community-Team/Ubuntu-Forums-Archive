---
title: "Rdesktop 100% CPU Utilization"
date: 2005-05-04
forum: General Help
---

### Post by xsdevnet on 2005-05-04
I've noticed that while running Rdesktop xorg is using 100% of my cpu.  I downloaded the source for 1.4.0 and recompiled it.  It has the same behavior as the earlier 1.3.1 version that comes with Hoary.  Any ideas where else to look?  Other than that I'm really pleased with my Ubuntu installation.

Thanks,
Steven

---

### Post by xsdevnet on 2005-05-05
I believe this was caused by playing the RDesktop windo on my secondary display.  It appears that the Nvidia driver only supports hardware acceleration on the primary display under linux.

Thanks,
Steven

---

