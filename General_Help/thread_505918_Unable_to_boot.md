---
title: "Unable to boot"
date: 2007-07-20
forum: General Help
---

### Post by beadwindow2001 on 2007-07-20
My brother was trying to download some synaptic packages for his computer. Half way through installation of packages his computer overheated and shut down. Now when I try to boot the OS it does not load and gives the following error:

[CENTER][   90.895946] bcm43xx_microcode5.fw not available or load failed.[/CENTER]

And once every few minutes it then gives another number. I left the computer on to see what would happen and it would give me the following numbers with nothing after that:

[CENTER]115.640404
139.674955
164.423525
288.863330
354.672001
411.708182
536.147929[/CENTER]

I am almost certain that it is having trouble booting because the packages he was trying to download did not fully load. I now need some direction on how to recover from this error. I hope that I have provided you with information that will be of some use. If you have any questions please do not hesitate to ask.

---

### Post by Kodfish on 2007-07-21
Try booting in recovery mode, it should say that in your grub. If you remember what the packages you were installing were, try "sudo apt-get remove $packages" and reboot.

---

### Post by beadwindow2001 on 2007-07-23
Thank you much. That solved the problem!

---

