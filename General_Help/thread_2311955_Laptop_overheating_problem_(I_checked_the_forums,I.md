---
title: "Laptop overheating problem (I checked the forums,I googled, I did the 101 stuff )"
date: 2016-01-31
forum: General Help
---

### Post by yannis3 on 2016-01-31
[B]Problem:
[/B]
Basically, my laptop is *far* hotter and *far *louder when I'm doing basic things like browsing Youtube/Reddit/Ubuntuforums etc when compared to Windows 7. 
Quite frankly this is the only reason why Linux isn't my main OS. The fans and the heat are just driving me nuts.


[B]Attempted solutions: 
[/B]
1) Bunch of jumps to multiple distros.  2) Using optirun   3) TLP   4) thermald
5) CPUfreq 6) top is perfectly normal 7) Graphics are running off integrated not dedicated
8) If windows can run quieter and cooler, then it's not the dust, stop. 

I very much feel frustrated and annoyed. I hope you can help, please. I don't really know what to do besides just using Windows for everything. 

[B]Relevant copy-paste from hardinfo summary:

[/B]-Computer-
Processor        : 8x Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
Memory        : 8012MB (2248MB used)
Resolution        : 1600x900 pixels
OpenGL Renderer        : Mesa DRI Intel(R) Ivybridge Mobile 
X11 Vendor        : The X.Org Foundation

if I run optirun then obviously it shows this:

OpenGL Renderer        : GeForce GT 650M/PCIe/SSE2

---

### Post by Petro Dawg on 2016-01-31
What is the brand and model of the laptop you are using?  By "Bunch of jumps to multiple distros", do you mean you just tried different flavors of Ubuntu/Mint or did you go the full mile and install something like Fedora?

---

### Post by yannis3 on 2016-01-31
It's Acer V3-771G. I tried Ubuntu and its various flavors,  Fedora and Debian. No difference. 
Do I get any points for messing with Arch on VM? No? Well, okay.

---

### Post by Petro Dawg on 2016-01-31
*Points awarded for trying Arch*  :p

I checked reported Linux compatibility with you laptop here... [http://www.linlap.com/acer_aspire_v3-771g](http://www.linlap.com/acer_aspire_v3-771g)
For the most part it seems it should run well, however there are 20% that reported it Poor or Unusable (whatever that means)

I noticed you stated "7) Graphics are running off integrated not dedicated".  Does your laptop have the dedicated Geforce chip, and is Windows using it when you are making the temperature comparison?  What happens when you install the additional drivers and run off the dedicated GPU?

---

### Post by yannis3 on 2016-01-31
Chrome isn't running off GeForce in Windows or at the very least it isn't showing that it is. Anyways, I tried running Chromium in Ubuntu using GeForce aka "optirun chromium-browser" 
and there's no difference. So yeah, I'm just as bummed as you are. I've also tried multiple different web-browsers (Chrome, Chromium, Firefox, even Midori), no difference there either.
 Ive tried multiple proprietary Nvidia drivers and no change there either.

---

### Post by blade4 on 2016-02-01
Unless you've already done so, I recommend you install an old version of ubuntu ( 10.04 or older ) or any linux. It'll help narrow down the culprit if it works. 

Also, although you mention point no. 7, I'd recommend checking the graphics setup a bit more.I say this because I have a somewhat similar rig as yours( MSI GT70 ) and my laptop always overheats when I use the linux nVidia driver ( its a GTX 670M card ). Right now I'm using the noveau driver and have no issues.

---

### Post by mastablasta on 2016-02-01
if i understand the issue appears when using Intel drivers. 

it could be a BIOS setting that Windows can use but Linux can't. also it might be possible that fan speed is set at constant rate thater than adjusting itself. there are various switches in the Intel drivers you should look into.


e.g. and a bit off topic my HP has AMD. In windows HP provides some HP super cool or something like that. it is really quiet and cool. now in Linux it all works but it is also louder.  funny thing some users had issue when upgrading to win10. apparently this function is no longer avialable for some models, so it would get loud in Windows 10 as well.

back to your issue - this leads me tobelieve it is a drive issue - a parameter is not set or a specific firmware is missing (might not be available on Linux).

---

