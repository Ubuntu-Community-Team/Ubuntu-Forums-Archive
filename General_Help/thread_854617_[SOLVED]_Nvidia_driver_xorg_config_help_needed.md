---
title: "[SOLVED] Nvidia driver/ xorg config help needed"
date: 2008-07-09
forum: General Help
---

### Post by MDSmith2 on 2008-07-09
Hello.
I am trying to set up xubuntu and all is good but the nvidia driver.
I have installed (using envyng) the nvidia 96.x.x driver for my nvidia Geforce 4 mx card (the nvidia site said to use the 96.x.x driver) and the driver is nistalled but it justs flashes three times without starting x then takes me to the low grapics mode. I am guessing that the problem is in my xorg.conf. here it is

---

### Post by MDSmith2 on 2008-07-09
Anyone?

---

### Post by bodhi.zazen on 2008-07-09
```
gksu nvidia-settings
```

Make your changes, save changes, restart X

---

### Post by MDSmith2 on 2008-07-09
I can't use the nvidia driver, it won't work so I end up falling back to the nv driver. I played around with it and it seems its the driver and not xorg.conf.

---

### Post by bodhi.zazen on 2008-07-09
You need to first remove the open source (nv) driver (nvidia-glx).

Then re-install the proprietary nvidia driver.

Then re-start X

---

### Post by MDSmith2 on 2008-07-10
Odd, I did a fresh install (corrupted filesystem, don't ask how) and the driver works now.
thanks

---

