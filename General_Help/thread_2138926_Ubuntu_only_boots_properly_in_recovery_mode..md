---
title: "Ubuntu only boots properly in recovery mode."
date: 2013-04-25
forum: General Help
---

### Post by bismuth92 on 2013-04-25
I have recently re-installed Windows XP on my system, and I am trying to get Ubuntu working again. I managed to get grub up and running again by booting from the install cd and re-installing grub. Now I can boot ubuntu in recovery mode perfectly. However, when I try to boot in regular mode, it gets as far as the log in screen, then when I enter my password, I get my background and nothing else. The top and side bars that I am used to are gone. I am guessing it is something to do with the graphics settings, but I don't know what to change. Any ideas?  I am running Ubuntu 12.04 on a Dell Vostro 1400. If you need more information about my system, please let me know what to type in to the terminal, as I am a little clueless about this. Thanks very much.

---

### Post by grahammechanical on 2013-04-25
Do you use Recovery Mode Resume? That loads Ubuntu without video drivers. Or rather, with the Nouveau open source driver. Here is what you can do.

Right click the desktop and select Change Desktop wallpapers. That should open System Settings. There you should see the Additional Drivers utility. You can use that to activate Nouveau or experiment with a proprietary video driver.

Regards.

---

### Post by bismuth92 on 2013-04-30
Thanks very much, that's helpful. I still can't get it to work, because I have now found out that it won't connect to the internet (even with an ethernet cord) so I can't play with drivers, but that's a whole other barrel of fish. Thanks again.

---

