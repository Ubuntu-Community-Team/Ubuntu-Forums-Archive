---
title: "Edgy wireless fixed ?"
date: 2006-10-26
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-10-26
Hey I was wondering if the Edgy wireless issues were fixed. I have a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) card. Has anyone gotten this card to work in Edgy ?

---

### Post by beerfan on 2006-10-26
The "known issues" sticky thread indicates that wireless is still broken for a lot of (Atheros at least) cards. If your card isn't Atheros based then you may be ok.

Silly me for buying an Atheros card :-( All the reading I did before buying indicated that it was well supported but I've had nothing but problems with it and Ubuntu.

---

### Post by Monkus on 2006-10-26
> **beerfan said:**
> The "known issues" sticky thread indicates that wireless is still broken for a lot of (Atheros at least) cards. If your card isn't Atheros based then you may be ok.

Silly me for buying an Atheros card :-( All the reading I did before buying indicated that it was well supported but I've had nothing but problems with it and Ubuntu.

My Atheros card worked great in Dapper, but I had a really hard time getting it to work in Edgy. But, I did get it to work, let me tell you how I did it.

First, I uninstalled Linux-restricted-modules
Then, I downloaded the madwiwi-old drivers
Then, I installed them
Uninstalled network-manager-gnome
restarted
inserted my ESSID and password into the Admin=>Networking
Whaaa La. 

I am rather a newb and so I probably haven't given you all the information you may need, but if you look at this thread

[http://ubuntuforums.org/showthread.php?t=241131&highlight=changing+madwifi](http://ubuntuforums.org/showthread.php?t=241131&highlight=changing+madwifi)

That is where I found information on changing the madwifi to the old ones. 
Anyway, I sure hope this helps you guys. Good Luck  :D

---

### Post by beerfan on 2006-10-26
That's interesting. The primary reason I'd want to upgrade my laptop from 6.06 would be to fix the problems with network-manager though and if I have to stick with the current version I will just wait until they fix the bugs in Edgy (if they fix them).

---

