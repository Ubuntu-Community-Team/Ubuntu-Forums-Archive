---
title: "Ubuntu 18.04 server on a Terastation"
date: 2018-06-09
forum: General Help
---

### Post by mdphoenix on 2018-06-09
I have a TeraStation which originally ran Windows Storage Server 2008.  I couldn't find a reload flash image for the unit so I tried multiple distros.  OpenMediaVault, FreeNAS, etc.  All of them crashed after running for a few days.  I figured I'd go with Ubuntu and learn a little bit in the process.  I now have 18.04 running on this guy with an MDADM RAID6 array.  The OS is running on a USB hard drive so all of the 6 drives can be used for the RAID.  Every few days, I'm still getting a crash.  I'm sorry if I'm not using the right term.  I get a bunch of information on the screen and the unit is frozen.  I have no GUI installed.  I have been using SSH and Webmin exclusively.  The unit crashed more often when I had a GUI.  Once I figured out how to configure it via SSH, I reloaded the unit and did not install a GUI.  The crashes are less frequent, but still there.  

I did find that the unit had a DIMM slot so I upgraded it from 2 to 4 GB.  The box is running an Atom D510 and 4GB of RAM.  I've run memtest on it for days on end and it never fails.  I'm not sure what the problem is.

Attached are two pictures of the screen when it dies.  Please excuse any incorrect terms I may have used or lack of information.  I am a complete Linux novice.  Thanks for any advice.
[ATTACH=CONFIG]280060[/ATTACH][ATTACH=CONFIG]280061[/ATTACH]

---

