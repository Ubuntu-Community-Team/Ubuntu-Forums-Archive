---
title: "Manual NVidia Geforce 6 series install  please help!!"
date: 2008-06-19
forum: General Help
---

### Post by Chevelu on 2008-06-19
Hello, I've installed ubuntu 3 days ago and first installed the Hardy Graphic drivers but the game lbreakout2 game was lagging...
So I installed Nvidia driver from the Nvidia web site. I installed it and rebooted my resolution is fine and lbreakout2 not lagging... but I can't activate desktop effect because they tell me I need my 3d acceleration graphics driver. 

Can someone tell me what I did wrong?

---

### Post by Deutscher Alex on 2008-06-19
Try going to System > Administration > Hardware Drivers, and check if the nVidia driver is activated

---

### Post by stchman on 2008-06-19
> **Chevelu said:**
> Hello, I've installed ubuntu 3 days ago and first installed the Hardy Graphic drivers but the game lbreakout2 game was lagging...
So I installed Nvidia driver from the Nvidia web site. I installed it and rebooted my resolution is fine and lbreakout2 not lagging... but I can't activate desktop effect because they tell me I need my 3d acceleration graphics driver. 

Can someone tell me what I did wrong?

The package nvidia-glx-new is all you need.  You can install that package by either enabling it in the restricted driver manager or through Synaptic.

---

### Post by Chevelu on 2008-06-20
should I install all nvidia-glx-new package or only the first one?

And deutscher Nvidia is not activated but if I do and reboot, the system switch into low resolution mode...

---

