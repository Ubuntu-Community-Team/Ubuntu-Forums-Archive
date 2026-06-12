---
title: "VNC (Vino) incredibly slow after installing proprietary graphics drivers"
date: 2016-03-26
forum: General Help
---

### Post by lakeshore2985 on 2016-03-26
Vino server has been utterly slow after installing AMD's proprietary graphics drivers for Linux Mint 17.3. I'm sure it has nothing to do with compression levels or vino settings, as everything was working fine before installing proprietary drivers for my graphics card.

I use xtightvncviewer client to access other computers remotely.

---

### Post by TheFu on 2016-03-27
VNC requires the use of a full VPN to be secure. The 'built-in' security for VNC is not sufficient.  I'd look into performance issues with the VPN and resolve those before looking any further.   vnc-server has a --localhost option to prevent users from connecting without using a VPN. This is by design.

Mint is not an "official" flavor of Ubuntu - but if you spelled out which Ubuntu it is based on, perhaps someone can help?  I know there were issues with support of the Radeon drivers in UIbuntu.  Exactly which driver is being used? How was it installed - PPA?

---

### Post by lakeshore2985 on 2016-03-27
No, it has nothing to do with VPN or security. I'm simply remotely accessing my computers inside my local network, therefore it has nothing to do with Vino configs. I'm pretty sure it is a problem with the graphics card drivers or Xorg or something. I just did a test, uninstalled all the third-party drivers and it's all good again.

 I was just wondering whether somebody had an idea why this is happening.

---

