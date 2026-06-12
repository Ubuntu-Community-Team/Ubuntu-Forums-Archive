---
title: "Only one core?"
date: 2007-01-04
forum: General Help
---

### Post by HarrisonHopkins on 2007-01-04
I have an Intel Core 2 Duo T5600 processor in my laptop. A dual-core processor. However, in Kubuntu, System guard seems to only display one core. How can I get it to use both cores?


Also, why does it always say that my processor is only running at around 998MHz when it is supposed to be at 1.83GHz? This is in Windows, and the BIOS.

---

### Post by Fully216 on 2007-01-05
I wonder if this is because of the speed step technology (Intel) or powernow (AMD) ramping the clock speed?

---

### Post by mcduck on 2007-01-05
In Dapper you need to use the right kernel to get support for multi-core CPUs. For you, the right package is 'linux-686-smp'. Install that & reboot and your both cores should start working.

And yes, the speed thing is because Ubuntu by default runs CPU's at minimum speed, automatically scaling the speed up when needed.

---

### Post by HarrisonHopkins on 2007-01-05
The speed also appears like that in the BIOS and in Windows. It doesn't only happen in Kubuntu.

I'm installing the other kernel now though.

---

