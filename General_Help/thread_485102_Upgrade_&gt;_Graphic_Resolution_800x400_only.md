---
title: "Upgrade &gt; Graphic Resolution 800x400 only"
date: 2007-06-26
forum: General Help
---

### Post by krsna on 2007-06-26
Hello, 
after upgrading to 7.04 the resolution went  to 800x400 max whereas it was 1024x768 priorly... what happened?
Now running *sudo dpkg-reconfigure xserver-xorg* and trying to reconfigure the video driver i should select something. It presents VESA. The graphic device is a *82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device* from *Intel.*
How should i configure Xorg?

Thanks

---

### Post by krsna on 2007-06-26
OK problem fixed: for this chip i need to select i810 driver and allow all graphic resolutions, selected 17" monitor and tadaaa!

Ubuntu and i are friends again :D

---

