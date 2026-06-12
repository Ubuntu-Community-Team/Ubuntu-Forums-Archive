---
title: "How do I boot minus the Network icon in gnome?"
date: 2008-02-15
forum: General Help
---

### Post by jdix123 on 2008-02-15
I've installed a pcmcia wireless card through ndiswrapper, and I'm pretty sure I've isolated a problem I'm having at boot.  If the card is in the machine at boot, x crashes and I just get a blinking cursor.  If I eject the card and boot normally, my system starts fine -- and when I push the card in, the computer hard locks.

If I boot to the recovery kernel, it works fine -- and something I noticed was that the little network icon in the top panel is absent.  I've configured the network and the card manually through iwconfig, so I don't need the gnome network manager to run, but I don't know how to turn it off.

Oh yeah, running gutsy.

---

### Post by strabes on 2008-02-15
System > Preferences > Sessions

Scroll down and uncheck "Network Manager." Then click on "Close." nm-applet will not start up the next time you log in.

---

### Post by jdix123 on 2008-02-15
Ok so I managed to remove it.

But now I don't seem to be connecting at all.   

Running iwconfig yields an ESSID, a Bit Rate, and a Link quality, signal level, and noise level.

System - administration - network shows the wireless network configured correctly with ESSID, WEP key, and DHCP.

No network in firefox.  What gives?

---

