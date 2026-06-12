---
title: "Very slow and with flickering black screen"
date: 2015-08-28
forum: General Help
---

### Post by enzo7 on 2015-08-28
Hi everyone, I'm new here in linux and today i've installed Kubuntu 15.04 and i figured out that is running slower than windows 7 (which was running perfectly) and i dont know why. I've tried with the 64 bits version and it was impossible to do anything, now i switched to the 32 bits version and is a little bit faster but it's still slow... very. Also I get a blinking black screen when opening "system settings", muon or while login session for example. 
I use the web browser a lot, normaly chrome with almost 10 tabs always, and in windows i've never had any issue, even in sessions with +12 tabs per browser (2 or 3 of them) which is pretty normal to me, but here it's been difficult to even open 3 or 4 tabs in firefox. 
I have an Athlon 64 4200+, 4 gb of ram and onboard graphics (ati x1200). Yes, I have a old pc but I've never had any problem running windows. I also tried with Linux Mint KDE 64 bits an it's slow too. 
I don't know what it is, hope you can help me. :)

---

### Post by mastablasta on 2015-08-28
I know what it is. the proprietary drivers for your GPU chip were dropped by AMD (previous ATI). the replacement open source drivers give the performance you see. 

RS600/RS690/RS740           Radeon X1200/X1250/X2100

solution - use windows 7 - you have good drivers under that OS and as you say it works really well and fast. the OS is also still well supported. note that you might face similar issue if you decided to upgrade to windows 10 (unless AMd provides drivers for win10 for that chip - but AFAIK these were moved to legacy in windows as well. windows 7 kernel is from 2009, Kubuntu 15.04 is from 2015. I wouldn't bother with Kubuntu anymore in your case. you can try it later maybe when 16.04 comes out if they fixed the driver but they probably wont. 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/)

---

### Post by mörgæs on 2015-08-28
Before leaving Buntu I suggest that you try X/Lubuntu.

---

