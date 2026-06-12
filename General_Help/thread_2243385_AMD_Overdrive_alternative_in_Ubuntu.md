---
title: "AMD Overdrive alternative in Ubuntu"
date: 2014-09-08
forum: General Help
---

### Post by sega2 on 2014-09-08
Hi, I just switched from Windows. My vga is R9 290x, which normally run 90c on high load, so back then in Windows I usually underclock this a bit (reduce voltage, limit the max temperature) which can be done with AMD Overdrive. 

Now that I'm dualbooting with Ubuntu, is there alternative to AMD Overdrive in ubuntu? Where I can underclock my gpu, limit the max temperature, and fan speed control? Since im planning to do some game in this OS, which without underclocking, it can go 90c. 

I have browsed around and found this [http://sourceforge.net/projects/amdovdrvctrl/](http://sourceforge.net/projects/amdovdrvctrl/) but it seems it's not updated. I have installed it and it wont work with my R9. Thank you

---

### Post by sotiris2 on 2014-09-08
Hello there. What drivers are you using? Open source or catalyst? Usually in ubuntu you can use [lm-sensors]("https://help.ubuntu.com/community/SensorInstallHowto") to monitor temperatures, and psensor is a simple interface for it with warnings, graph etc.. 
 
You can use this to check if your card is actually hitting these temperatures. If you wish to lower temperatures I 'm not sure you can actually undervoltage the card via the OS like in windows (probably with specific driver from your card supplier). However you can try and use a more conservative profile to avoid high temperatures. Check [this]("https://help.ubuntu.com/community/RadeonDriver") and for more info follow the link to the x.wiki in that page.

EDIT: And ofcourse if you install the proprietary catalyst drivers.. You can install overdrive since it has a linux version.

---

### Post by sega2 on 2014-09-08
> **sotiris2 said:**
> Hello there. What drivers are you using? Open source or catalyst? Usually in ubuntu you can use [lm-sensors]("https://help.ubuntu.com/community/SensorInstallHowto") to monitor temperatures, and psensor is a simple interface for it with warnings, graph etc.. 
 
You can use this to check if your card is actually hitting these temperatures. If you wish to lower temperatures I 'm not sure you can actually undervoltage the card via the OS like in windows (probably with specific driver from your card supplier). However you can try and use a more conservative profile to avoid high temperatures. Check [this]("https://help.ubuntu.com/community/RadeonDriver") and for more info follow the link to the x.wiki in that page.

EDIT: And ofcourse if you install the proprietary catalyst drivers.. You can install overdrive since it has a linux version.

Hello, yes im using amd catalyst driver in my ubuntu, but when I opened catalyst control center i cannot see overdrive options where i can config undervolt and such there [-o

---

### Post by QIII on 2014-09-08
Hello!

The Overdrive functionality is largely mdonissing from the CCC AMD has made available for Linux.  That being the case, opensource developers have to peer into a black box to try to sort out how to make things work.  That takes time.

Remember that drivers are provided by the OEMs, not by the distributors of OSes.  Not even Microsoft.  They don't write ATI drivers.  ATI does.

Your card is very new.  It is likely that the developer is working on it, but it won't be done overnight.

---

