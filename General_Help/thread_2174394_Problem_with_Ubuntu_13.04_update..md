---
title: "Problem with Ubuntu 13.04 update."
date: 2013-09-14
forum: General Help
---

### Post by Pengwyn44 on 2013-09-14
On 06/09/13, I responded to an update for Ubuntu 13.04 by clicking on the update icon called Software Updater.  After the requested re-boot my computer became in effect unusable, because the background filled the screen entirely and therefore I could not see any icons nor the top menu.

I have an older computer running 13.04 with no problems at all!

The hardware differences are as follows:

Old Machine                                                                

Processor (CPU) Intel Core 2 Duo E7500 (2.93Ghz)       
Motherboard ASUS P5QPL-AM
Memory 4GB CORSAIR
Graphics Card 512MB ATI RADEON HD 4350 PCI EXPRESS

 New Machine

Processor (CPU) Intel Core i3-3220 (3.30Ghz)
Motherboard ASUS P8H61-MX
Memory 4GB SAMSUNG DUAL-DDR3
Graphics Card 1GB ATI RADEON HD6450

Is this a Hardware problem please?

---

### Post by grahammechanical on 2013-09-14
It may be a video driver problem. All I suggest is that you right click the desktop and select Change Desktop Background. That will open System Settings in the Appearance utility. From there you can get to the full set of System utilities. Load Software and Updates and open the Additional Drivers tab and experiment with the available video drivers. Wait a few secconds for the utility to find video drivers.

You can also select Recovery Mode>Resume. You will find Recovery Mode in 13.04 in the Advanced Options for Ubuntu sub-menu of the GRub menu. Recovery Resume will load Ubuntu with an open source video driver designed for graphic cards that cannot support hardware video acceleration. It acts as a fall-back video mode in 13.04. If it gets you to a desktop you can then change video drivers.

Regards.

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **General Help**.*

***Installations & Upgrades*** is for support installing and/or *upgrading* Ubuntu to a newer release. ;)

---

### Post by Pengwyn44 on 2013-09-16
Thank you for your suggestions. The first one I cannot use because the Software & Updates icon does not do anything when I click on it!
The second one brings me to the desktop, but unless there is another way to change the drivers other than the icon I am no further on.
Is there a way of changing the driver using the Terminal? Or would I be better off re-loading the OS?

---

### Post by Pengwyn44 on 2013-09-18
Eventually I had to replace the graphics card with an ATI Radeon HD 4350. It was the only way to resolve the issues that kept re-appearing when software changes were made.

---

