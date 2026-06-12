---
title: "I need help with my Nintendo DS usb wifi connector"
date: 2007-10-14
forum: General Help
---

### Post by JESSU on 2007-10-14
I have rad the other posts but I couldn't follow. Not sure if this will help you help me but..I typed lsusb in the termanl and got this.
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:0401 Hewlett-Packard ScanJet 5200c
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0411:008b MelCo., Inc. 
Bus 001 Device 003: ID 046d:c510 Logitech, Inc. 
Bus 001 Device 002: ID 0409:0050 NEC Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by runemaste644 on 2007-10-14
That would be nice to get that to work. I will look for a driver.

---

### Post by JESSU on 2007-10-19
Does 7.10 have anything that will help with this?

---

### Post by JESSU on 2007-11-03
bump

---

### Post by lfaraone on 2007-11-29
bump

---

### Post by saxamo on 2007-12-10
I don't think it's possible to work :(

---

### Post by Pridkett on 2008-02-04
Providing a bit more context may be helpful.  Are you trying to use the wifi adapter so your DS can get on the internet or are you trying to use it as a normal WiFi device in Linux?  If you want to use it as a norma wifi device, you'll be interested in the work of the [rt2x00 project]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page") which provides open source drivers for the card.  Of note, linux 2.6.24 is the first version to have support built in for the driver, so you'll be in for an adventure.

If you'd just like to share with your DS and aren't particular about how, see section 4.1 of the [Nintendo DS Wireless Networking Guide]("http://www.gamefaqs.com/portable/ds/file/925329/40161") as that provides some help on the topic.

---

### Post by crazytim87 on 2008-02-27
Would that driver happen to work the same if you wanted to connect you Wii using the adaptor?:confused:

---

### Post by OttoDestruct on 2008-03-06
[This](http://ubuntuforums.org/showthread.php?t=640083) is the only way I have been able to get it to work.

---

