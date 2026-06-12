---
title: "Applications Menu problem after upgrade to Ubuntu 6.06"
date: 2006-07-15
forum: General Help
---

### Post by secondvijai007 on 2006-07-15
Hello! 
      I've been using Ubuntu for quite some time now, and just recently I decided to upgrade to the newest version, dapper drake. The upgrade itself went fine, and I was able to boot in properly into ubuntu without any problems (well, i had to play around with the xorg.conf file, but its ok now) There were however, a few problems that arose once I logged into ubuntu. 
      For some odd reason, the Applications menu flickers crazily when I click it, and this menu bar takes up over half of my processing power (I'm refferring to the blue process utility that I have on my panel). The "Places" and "System" menus seem fine. After say 30 minutes, this problem goes away, but until then I'm unable to access anything from the applications menu.
      Another issue that I'm having is that my network card is no longer being recognized after the upgrade (it refuses to turn on). I've checked the ndiswrapper configurations, but I can't seem to figure out what is wrong. When I type iwconfig to see a list of network connections, I'm finding that there is no wlan0 connection even available.
      I'm willing to try anything... so please make any suggestions as to how to fix this. I'm starting to think this upgrade was a bad idea.....

Thanks

---

### Post by bionnaki on 2006-07-15
I think upgrading is trouble, at least in my experience. you should have done a fresh install.

---

### Post by secondvijai007 on 2006-07-15
I've found a solution... well, kind of. I just copied a fresh copy of the sources.list for dapper and then simply upgraded my computer. One of the packages apparently has a fix to the applications menu problem. 

I'm still struggling to find a solution to the wireless network card problem (no wlan connection) So i'd really appreciate any help. Thanks!

---

### Post by bionnaki on 2006-07-15
what card?

---

### Post by secondvijai007 on 2006-07-15
What i have is a wireless pcmcia card from motorola. It is supported by ndiswrapper, and i had it running when I was using breezy. If it helps any, i've found that the wlan connection seems to be renamed as eth1. I'm having trouble getting the lights to come on on the card. i'll see if i can give you more information...

---

