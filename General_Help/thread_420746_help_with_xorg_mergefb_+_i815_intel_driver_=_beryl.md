---
title: "help with xorg: mergefb + i815 intel driver = beryl working?"
date: 2007-04-23
forum: General Help
---

### Post by harty83 on 2007-04-23
Hello,

I currently have a working copy of xorg.conf that utilizes xinerama to get a dual monitor setup (laptop and external LCD) working.  However, as you probably know, beryl will not work with xinerama.

I've read a bit about mergefb and that it should work with beryl but I cannot get it to work with my intel i945gm graphics card.  

Can anyone give me some guidance?

Thanks!
Alan

---

### Post by james_xl on 2007-04-29
i've got it working with my intel855

Section "Device"
	Identifier	"i810"
	Driver		"i810"
	BusID		"PCI:0:2:0"

        Option  "DRI"                           "true"
        Option "MergedXinerama" "yes"
        Option  "MergedFB"                      "true"
        Option  "MonitorLayout"                 "CRT,LFP"

        Option  "SecondPosition"                "RightOf"
        Option  "MetaModes"                     "1024x768-1024x768"
        Option  "SecondMonitorHorizSync"        "30-96"
        Option  "SecondMonitorVertRefresh"      "50-85"
        Option	   "UseEdidFreqs" "True"
        Option  "MergedNonRectangular"          "true"
EndSection

---

