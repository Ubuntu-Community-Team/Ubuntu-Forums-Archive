---
title: "Macbook/Macbook Pro Battery disappears after full drain"
date: 2013-04-22
forum: General Help
---

### Post by dbritt73 on 2013-04-22
I have two different Macbook laptop computers:

Macbook (2, 1)
Macbook Pro (3, 1)

I have done a clean install of Ubuntu 12.10 (replacing Mac OS X) on both machines (months apart from each other)
The first computer I did this to was the regular Macbook (2, 1). Everything installed great and all hardware (minus the iSight webcam) worked out of box. Even the battery worked great. However, I let the laptop run out of battery and fall asleep.
 
Ever since, there is no battery icon in the notifications area. When the laptop gets unplugged (which happens more often by accident than not due to the magsafe design) it will shut off automatically.
 
I have tried a few suggestions which include:
 
o   Resetting the NVRAM (which shouldn't have anything to do with the battery, but who hasn't trouble shot a Macbook and didn't reset the NVRAM)
o   Resetting the SMC (which should be what controls the battery)(this is a known issue with Mac, even when Mac OS X is the main OS)
o   Tried a different battery
o   Tried a different magsafe power adapter
o   I booted off of a Mac OS X 10.5.2 disk (pretty old at this point) when it booted, the battery icon would appear in the notification area. However it would still shut off immediately following it being unplugged.
o   I have also read that the max number of CPU cores affects this. I tried limiting the number of cores on boot to one. This also did nothing.
 
I found BAT0 listed under the file path:  /proc/acpi/battery/bat0. Presence = no and there is no other information given at this point (I have seen screenshots of what this file is supposed to look like and it is full of information).
 
This has happened to two different Macbook laptops, both clean install of Ubuntu 12.10 overwriting Mac OS X. The battery worked initially both times; following a full drainage and wake from sleep did the battery disappear for both of them. I do not at this point think it is hardware related (I mean what are the odds of that!)

Any help or if you have seen this before let me know, it seemed that I could not find any sort of answer or forum tailored to this issue.

Thank you for your time!!

---

### Post by Musikaman on 2013-04-23
I don't know if this will help you at all, but I remember reading that there was a hardware level problem with the 2,1 macbooks and batteries... from Wikipedia: "[COLOR=#000000][FONT=sans-serif]There were problems with batteries on some models from 2007 not being read by the MacBook. This is caused by a logicboard fault and not a fault with the battery."

I have the same model... and I've tried getting help around here for a couple things. I don't suppose you tested your SPDIF out while Ubuntu was loaded? :) I'm trying to figure out if I'm having a hardware level problem or software... and I'm being lazy about reinstalling OSX o figure it out. lol[/FONT][/COLOR]

---

