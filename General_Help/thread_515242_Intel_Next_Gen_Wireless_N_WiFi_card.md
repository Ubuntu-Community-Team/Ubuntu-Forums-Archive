---
title: "Intel Next Gen Wireless N WiFi card"
date: 2007-08-01
forum: General Help
---

### Post by Scubastev013 on 2007-08-01
Hey everyone,

I have a Dell E1505 that originally had Vista on it.  I've made the switch and everything is working great!  There is one thing that I could not get working though.  I have an Intel Next Gen Wireless N card in the laptop instead of the basic one.  Now, if I bought the same computer preinstalled with Ubuntu, I could only pick the basic wifi card.  Where can I find the drivers to  make this work.  I don't necessarily need it, but it would be nice to have.

Thanks in advance,

Scuba

---

### Post by testube_babies on 2007-08-01
You need a kernel with the mac80211 stack enabled and iwlwifi drivers installed:  "The mac80211 stack allows us to use the iwlwifi driver for intel 3945 and 4965 users...it is the only driver for the 4965 wireless chipset."

That's the new wireless stack in 2.6.22, so maybe it's enabled by default in Gutsy?


EDIT:  just found a guide [http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

---

