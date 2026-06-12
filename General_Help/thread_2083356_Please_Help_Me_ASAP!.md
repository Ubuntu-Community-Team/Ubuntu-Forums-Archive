---
title: "Please Help Me ASAP!"
date: 2012-11-12
forum: General Help
---

### Post by videogame57 on 2012-11-12
I need help very soon, I'm running lubuntu 12.10 and I am unable to correctly configure my nVidia FX 5400 graphics card. I have two monitors but on the first monitor when I set the resolution to the monitors native 1280x1024 and hit apply the box closes but there is no effect. Upon returning to the monitor settings I am back to 640x480. My second monitor is the identical model however I can change the resolution and my changes are remembered, the catch is my options top out at 840x480. I attempted to setup the nVidia drivers and ditch the crappy ones that come with lubuntu, but they didn't work. I need the two monitors setup to extend my desktop and have both at 1280x1024 ASAP.

(EDIT, I managed to get one display up to 1280x1024 and extend my desktop, but my second display is still stuck at 840x480)

---

### Post by TenPlus1 on 2012-11-12
Go into Terminal and type:

   sudo apt-get install nvidia-current

Reboot after install and run Nvidia Control Panel to setup dual-display...

---

### Post by videogame57 on 2012-11-21
Did you read the part where I said I installed those drivers and they didn't work? I was limited to pathetic resolutions.
I also don't need two monitors anymore.

---

