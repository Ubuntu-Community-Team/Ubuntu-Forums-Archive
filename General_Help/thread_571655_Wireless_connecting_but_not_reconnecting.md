---
title: "Wireless connecting but not reconnecting"
date: 2007-10-09
forum: General Help
---

### Post by Page on 2007-10-09
I've been having issues with my laptop wireless. (Broadcom 43xx chipset with ripped firmware running on the native kernel driver) 

At college, I am able to connect to the wifi network right after boot, but if I change my location too much, the connection is broken and I am unable to reconnect for awhile. 

Killing and restarting the NetworkManager process does nothing to fix this.

Any ideas?

---

### Post by strabes on 2007-10-09
Have you tried compiling ndiswrapper? I've done it on several friends' laptops with that exact card, and it seems to work quite nicely. Check out [this page](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) for a great howto.

---

