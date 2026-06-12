---
title: "Display &amp; Driver error"
date: 2007-07-14
forum: General Help
---

### Post by Kuukkeli on 2007-07-14
1) when i start up linux ubuntu or kubuntu, they're both pixel mess
A: Okay i changed nv->vesa to get this correct from xserver-xorg

so my latest problem is that when i install nvidia driver and enable it, then after that if i ever boot or shut down, linux crashes into black screen what i can type to. Could somebody help me to fix this bug?

---

### Post by dougfractal on 2007-07-14
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reconfigure X

Then use 
>System>Administation>Restricted_Drivers_Manager   to enable nvidia.

---

### Post by Kuukkeli on 2007-07-14
Thanks, i shall try that. =)

---

