---
title: "Ubuntu 12.10 Black Screen"
date: 2013-03-08
forum: General Help
---

### Post by Stryars on 2013-03-08
Hi,

And again, my third problem today: When I boot Ubuntu, I just get a black screen, no login session. But I have access to the ttyX console !
I tried to boot with the "low graphics mode", and it works. So I think it's a problem with my graphic card's driver... I have a Radeon HD 7850, and I'm using the "X.Org X Server" for the drivers.
Any idea :/ ?

Thanks,
Stryars

---

### Post by Stryars on 2013-03-16
Anyone ?

---

### Post by INTENSETUX on 2013-03-16
Had this problem whenever i upgraded , Boot Repair was the only solution that worked for me , [http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

Burn the image to disk and reboot into Disk Repair , choose 32 bits or whatever is relevant , you can try Recommended Repair to begin with but what i think helped me was Advanced options/Grub Options tab and select ''uncomment GRUB_GFX MODE(solves the out of range error)''

Hope this helps

---

