---
title: "Watching TV... howto? (I'm lost...) :("
date: 2005-10-17
forum: General Help
---

### Post by canglan on 2005-10-17
Hi folks,

Okay I am a bit lost here... I've been searching on this forum as well as google and some other forums.

All I want is to watch TV in Ubuntu Breezy, but it seems not that easy at all.

I am running Ubuntu Breezy on a normal 32bit system, with NVidia GeForce 5600 (nvidia-glx installed) and the latest kernel (2.6.12-9-k7).

My TV card is Hauppauge NOVA-t PCI (Philips TDA10045 / SAA7146), it's DVB-T. Well, I don't really know what these model numbers mean, but yeah that's what I get from dmesg and lspci. And dvb_core 82088 2 budget_ci,budget_core is the output I get from "lsmod | grep dvb".

I have tvtime installed, but I get Cannot open capture device /dev/video0: No such file or directory error. And MythTV is driving me insane too... >.<

I know it is quite an old TV card, but I expect it to at least work...

Does anyone have an easy-to-understand step-by-step instruction to set up my TV card and everything? Please don't just point me to some urls and sites, I swear I've been to many sites and tuts but still couldn't get a well understanding. I am very new to the TV card field.

By the way, I have ordered a VideoMate DVB-T300, it supports both analog and digital (Philips SAA713x), would that be any easier to install & config, etc?

Thank you in advance!

---

### Post by fut21 on 2005-10-17
Mybe thei howto would help you. Remember that it is at different chip, but it can perhaps give you an idea.
[http://www.ubuntuforums.org/showthread.php?t=24813&highlight=saa7134](http://www.ubuntuforums.org/showthread.php?t=24813&highlight=saa7134)

---

### Post by cyfer on 2005-10-17
[QUOTE=canglan]Hi folks,

Okay I am a bit lost here... I've been searching on this forum as well as google and some other forums.

All I want is to watch TV in Ubuntu Breezy, but it seems not that easy at all.

I am running Ubuntu Breezy on a normal 32bit system, with NVidia GeForce 5600 (nvidia-glx installed) and the latest kernel (2.6.12-9-k7).

My TV card is Hauppauge NOVA-t PCI (Philips TDA10045 / SAA7146), it's DVB-T. Well, I don't really know what these model numbers mean, but yeah that's what I get from dmesg and lspci. And dvb_core 82088 2 budget_ci,budget_core is the output I get from "lsmod | grep dvb".

I have tvtime installed, but I get Cannot open capture device /dev/video0: No such file or directory error. And MythTV is driving me insane too... >.<

I know it is quite an old TV card, but I expect it to at least work...

Does anyone have an easy-to-understand step-by-step instruction to set up my TV card and everything? Please don't just point me to some urls and sites, I swear I've been to many sites and tuts but still couldn't get a well understanding. I am very new to the TV card field.

By the way, I have ordered a VideoMate DVB-T300, it supports both analog and digital (Philips SAA713x), would that be any easier to install & config, etc?

Thank you in advance![/QUOTE]

i do have a similar little problem on a dvb-sat card 
i managed to make it work in vlc but not any other application ...zapping or tvtime

well , my sat card well known to make problems with linux systems ....
here is my advise ...and i think you can follow it and make your card work...

get the chip model of your card and search google to find what modules you need to probe ..to make it work 

when you done that ..look at dev/ for a dvb directory ......it should have 4 or 8 files
dvr0 , dmux0 , fronend0 and 1 ot 5 other files ......" i'm getting only 4 files...and that's why i'm having problems"

i think you should install VLC .... cause it will not allow you to scan...but at least it will give you a hint if your card works.....

..i can't give you specific help on what modules to probe ...cause i don't know your chip .....

modules are probed with 
#$ modprobe WhatEverYourModulesARE ###ex. dst ,bttv ....etc

i wish i knew more friend

---

