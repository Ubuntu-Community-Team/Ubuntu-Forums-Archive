---
title: "Display settings lost?"
date: 2015-03-25
forum: General Help
---

### Post by garyed on 2015-03-25
Everything has been fine for a couple months in 14.04 & just after trying to install Wine my display stopped working correctly. It's stuck at 1024x768 & there are no other options to choose from when i go to the display settings. I tried rebooting & even shutting down for the night but this morning nothing has changed. Any ideas?

Well I feel kind of stupid but I just did "apt-get remove wine" & "apt-get purge wine" to see what would happen. Even though it said wine was not installed, when I rebooted the display returned to normal (1920x1080) with all the different resolution options to choose from in the settings. So now I'm afraid to try & install wine again but i need it for a couple programs. Any ideas for this one?

---

### Post by dino99 on 2015-03-25
i does not think that wine should be blamed
but the graphic driver could be related to your issue: which card is used with which driver ?

---

### Post by garyed on 2015-03-25
> **9d9 said:**
> i does not think that wine should be blamed
but the graphic driver could be related to your issue: which card is used with which driver ?

I'm using the AMD/ATI: Cedar Radeon [HD 5000/600/7350 series] driver. The video card is: SAPPHIRE Radeon HD 5450 1GB 64-bit DDR3 PCI Express 

The only reason I think it has to do with wine is everything was running fine until I tried installing wine. I got some errors at first so i did an apt-get update & tried to install a second time. The second time it stopped at the O.K. screen after all the downloads & unpacking was finished. It still didn't install so I rebooted. That's when my display went haywire. I tried rebooting & then a total cold boot but nothing helped. There was no option in the display settings except 1024x768 & it did show the driver as installed. I turned the computer off for the night but still no change when i booted up in the morning. After I posted here I decided to uninstall & purge wine even though it showed as not installed. The purge did show some stuff deleted though so i rebooted & everything worked fine. I'm going to try & install wine again & see what happens. Any recommendations for installing wine? 
I just did:  "apt-get install wine"   By the way I'm using Ubuntu Studio 14.04

---

### Post by garyed on 2015-03-25
Update:
I installed Wine using synaptic & this time everything went smoothly. It installed fine & no problems with the screen resolution either. I tried rebooting just to be sure & all is O.K. It's obviously nothing with wine itself causing any screen problems but something must have happened during the botched installation that caused the problem. Even though wine didn't install it still removed some dependencies when i did "apt-get purge wine" that might have caused the problem. I guess i'll never know for sure but everything seems to be working O.K. now.

---

