---
title: "raspberry pi ethernet"
date: 2020-04-16
forum: General Help
---

### Post by hmiersch on 2020-04-16
Hello. 
I just installed Ubuntu on my raspberry pi. The problem is that the Ethernet does not appear in the settings app. Only the VPN and proxy settings appear but not the Ethernet. Do I have to edit some configuration file?

---

### Post by HermanAB on 2020-04-17
Raspbian is a Debian distribution for the RPi.  That would be the easiest way to get everything to work.

If you really want to rediscover all the funnies, the RPi Ethernet MAC/Phy is on the USB bus, so you probably need to start your investigations with lsusb.

---

