---
title: "Can't get into Ubuntu with new graphics card!"
date: 2007-10-21
forum: General Help
---

### Post by MaxL on 2007-10-21
I just switched graphic cards (from a Radeon 9550 to a NVIDIA Geforce 7600 GS OC) and now when I start up Ubuntu there's no way to get in because I get this blue and grey screen full of errors. Anyway I can fix this? I'm pretty sure there is a code you can use (because eventually the blue screen boots you into terminal) but I lost that code. This happened to me like 3 years ago when I went from my on board graphics to the Radeon 9550.

Probably has something to do with that I didn't uninstall the ATI drivers... >___>;; and now Ubuntu doesn't like the NVIDIA card. Anyway I can just uninstall those from terminal and then just run the basic graphics driver again?

---

### Post by Rumo on 2007-10-21
You need to reconfigure your xserver. You can do this with the following command:  'sudo dpkg-reconfigure -phigh xserver-xorg'.

---

### Post by Wiebelhaus on 2007-10-21
> **Rumo said:**
> You need to reconfigure your xserver. You can do this with the following command:  'sudo dpkg-reconfigure -phigh xserver-xorg'.

Just to reiterate Rumo's good advice.

---

