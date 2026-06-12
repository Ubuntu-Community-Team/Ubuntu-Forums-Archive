---
title: "Cant adjust brightness pavilion 1035dx"
date: 2013-02-07
forum: General Help
---

### Post by cloroxX on 2013-02-07
Hello I recently got a new laptop and i've always loved linux, although i cannot run it on my desktop because im running a HD 7750 which is currently unsupported =/

Anyways I cant adjust my brightness settings on this laptop im running 12.10, manually in setting, or with the shortcut keys. Shortcut keys make he brightness bar in top right corner pop up though.. I've tried all solutions on this page [http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g](http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g)

The first suggestion removes my brightness settings all together the one with "acpi_backlight=vendor" 

The other 2 I have no luck with =/ Hoping for some help :D

---

### Post by Stonecold1995 on 2013-02-07
I think the HP Pavillion might not be able to adjust brightness while running Linux.  My brother has an HP Pavillion dv6 and it is also unable to adjust screen brightness (the brightness level itself can be changed, but the actual brightness doesn't change).

---

### Post by cloroxX on 2013-02-07
That sure is a bummer =/ ill just start carrying my charger everywhere then :P Thank you for the info!

---

### Post by Stonecold1995 on 2013-02-08
If you're worried about power usage, there are plenty of ways to lengthen battery life.  I've heard that a laptop screen only uses about %50 of the total energy being consumed by the computer, most of the rest is used by the processor(s).  Just look up ways to increase battery life, you'll likely be able to compensate for a screen stuck on bright.

---

### Post by cloroxX on 2013-02-08
haha 50% seems like a lot to me! >_< I will look into that although, im finding my battery to be almost dead after one of my 2 hour classes!

---

### Post by cloroxX on 2013-02-08
hey i just fixed it by accident on attempt of creating a virtual machine on virtual box haha, ended up loading a propriety driver for my laptop which was giving me problems at first in which I managed to fix with kernel related issues during the same process, figured "hey maybe ill try the brightness fix on this new driver" and wallah! Rebooted and now I can adjust brightness! I just used the "acpi_backlight=vendor" fix, figured it was worth a shot with the new drivers loaded :D

---

### Post by Stonecold1995 on 2013-02-08
> **cloroxX said:**
> hey i just fixed it by accident on attempt of creating a virtual machine on virtual box haha, ended up loading a propriety driver for my laptop which was giving me problems at first in which I managed to fix with kernel related issues during the same process, figured "hey maybe ill try the brightness fix on this new driver" and wallah! Rebooted and now I can adjust brightness! I just used the "acpi_backlight=vendor" fix, figured it was worth a shot with the new drivers loaded :D
What steps did you take to do that?

---

### Post by cloroxX on 2013-02-08
nothing complicated... just dkms and headers haha what happened was the first time I tried propriety video driver it wouldn't work correctly so then I got headers then I went ahead and went to the ATI catalyst website, downloaded the driver there and installed it in terminal which I then figured out was a mistake because it really messed my GUI up.. dont know why. But this time I simply did the same install of the dkms and headers and went ahead and just used the propriety driver there and it actually loaded where as the first time I tried to use the propriety driver before loading dkms and headers and that is why it had never worked for me.. or so I thought, I just did the whole thing backwards =/

---

