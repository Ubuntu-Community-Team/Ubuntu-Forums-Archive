---
title: "Power management kodibuntu"
date: 2015-06-03
forum: General Help
---

### Post by nik13 on 2015-06-03
Im new to linux/ubuntu and am trying to build a media center/server ive gone with kodibuntu and have shares all setup amd it works great for what we want it to do. But now advancing on refining the build/setup we want to make the pc hibernate on idle. We can make it hibernate but when streaming something from it on another pc it will just hibernate. Ive tried using dconfig to setup power options to get this to work and also tried settings in the kodi media player side to no avail. Any help on this would be amazing.

---

### Post by TheFu on 2015-06-05
Don't think it does this, built-in.  You'd need to create a script that watches network traffic and hibernates if there isn't any.

I gave up on standby/hibernation because the system wouldn't wake up based on input from the remote (USB connection) on my system.  I think all the power settings are highly dependent on the motherboard and BIOS involved.

Sorry - don't have anything more.  My Kodi box is a central part of my network (NFS, apt-cacherng, etc) an uses less than 20W, so power use isn't too important.  I've considered moving the Plex Server part off to another machine along with NFS, apt-cacherng, etc so the kodi box doesn't do anything except run Kodi with PlexBMC and US-FreeCable plugins. Alas, more important things need to happen on my honey-do list first. ;(

---

