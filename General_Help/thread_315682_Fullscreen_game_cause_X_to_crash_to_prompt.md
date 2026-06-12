---
title: "Fullscreen game cause X to crash to prompt"
date: 2006-12-09
forum: General Help
---

### Post by qiemem on 2006-12-09
Recently wiped and reinstalled (now running Linux Mint, pretty much Edgy with proprietary codecs). I installed nvidia drivers via the envy script, and that seemed to go fine (beryl works... mostly, and I get nvidia-settings working fine too). Then I installed Nexuiz, Tremulous, and some others off the repos. Whenever I try to play any of the games that load to fullscreen, X just crashes... I get a prompt saying connection to the X server has been lost, plus other stuff. I can't tell if the problem is with the nvidia drivers or what. Any help would be most appreciated.

---

### Post by themerchant on 2006-12-12
Im having the same problem ](*,) ](*,)

---

### Post by chojin on 2006-12-21
check and see if your driver is 1.0-9629.

I had this problem with this driver, and found a whole bunch of people who did also... time to update from [www.nvidia.com](www.nvidia.com)!

---

### Post by qiemem on 2006-12-22
Yep, I have 1.0-9629. I used the envy script to install, which downloads directly off the nvidia website. So yeah. Did you have to do anything else to get it set up correctly?

---

### Post by qiemem on 2006-12-22
Woohoo! Okay, so upgrading to the beta drivers via this guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)
did it for me. I was messing up earlier because when I would try to uninstall my current drivers via envy, i would go to terminal with ctrl-alt-f1 and then uninstall and reinstall with aptitude. Then I would try "startx" to get back into x. That would of course error, saying that I had a version mismatch. But that's because it was using the version from what X was just running (or something like that). So I just had to restart and everything works great now. Doh!

Thanks though, you got me thinking down the right path.

---

