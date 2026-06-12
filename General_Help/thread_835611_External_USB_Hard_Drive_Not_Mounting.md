---
title: "External USB Hard Drive Not Mounting"
date: 2008-06-20
forum: General Help
---

### Post by lonelypauly on 2008-06-20
I cannot get my external usb drive to mount.  Im using Kubuntu Hardy (KDE 4) and my usb hard drive has 2 FAT32 partitions and 1 NTFS partition.  The entire device is not mounting at all, but it shows up when i run lsusb (its the Seagate device btw):

lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 006: ID 0bc2:3000 Seagate RSS LLC 
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 005: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

Is there a way I can get my seagate drive to automount?  The "Recently Plugged Devices" notifier/applet is totally useless in Kubuntu and does nothing at all.
Any help would be greatly appreciated!

---

### Post by geo909 on 2008-06-20
Is that a seagate *freeagent* drive?

If yes, do you have problems mounting the disk when it's freshly plugged in?
I mean, try to unplug it and it replug it again..
Does it mount now?

Sorry, it seems a stupid answer, but freeagent drives have a certain problem on Linux.Search in google or here for "seagate freeagent drive spindown problem". Nothing serious, but it's really annoying..

---

### Post by lonelypauly on 2008-06-20
ah, that is good to know!  i plugged it in a few times and it finally came up!  thank you so much!

---

### Post by geo909 on 2008-06-20
The thing with freeagent drives is that if you let them idle for 20 minutes (even less, I don't remember) then it get's in a standby mode and it is unusable. That's only in linux. 

 There's a lot of discussions going on for that matter. For example take a look at [this]("http://ubuntuforums.org/showthread.php?t=796814&highlight=seagate+freeagent").

---

