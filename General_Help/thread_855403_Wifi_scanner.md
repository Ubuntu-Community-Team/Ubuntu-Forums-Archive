---
title: "Wifi scanner"
date: 2008-07-10
forum: General Help
---

### Post by enchance on 2008-07-10
What tool is there which allows me to scan for open wifi signals especially those with hidden SSIDs?

---

### Post by forger on 2008-07-10
not sure, but:
sudo apt-get install wifi-radar rutilt

system > administration > rutilt
applications > internet > wifi-radar

---

### Post by toolzen on 2008-07-10
You could try:

# sudo iwlist wlan0 scan

Substitute wlan0 with the name of your wifi card. I would also do it with the | more pipe if you have lots of wireless networks around you.

---

### Post by enchance on 2008-07-10
> **forger said:**
> not sure, but:
sudo apt-get install wifi-radar rutilt

system > administration > rutilt
applications > internet > wifi-radar

Thanks! Are there any more by chance?

---

### Post by forger on 2008-07-11
no, not for gnome that i know of :)

> apt-cache search 'wifi|wireless'

---

### Post by mybeat on 2008-07-11
Kismet can be used to

---

### Post by fragos on 2008-07-11
Caution: running multiple network managers can cause problems. They both think they're the only one and interfere with each other. If you install wifi-radar you'll need to disable the current network manager in sessions or edit that entry to start wifi-radar instead of nm-applet. I don't know if this issue has been considered in 8.04 which uses nm-applet by default.

---

