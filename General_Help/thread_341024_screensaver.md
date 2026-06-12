---
title: "screensaver"
date: 2007-01-18
forum: General Help
---

### Post by SonicBOOM on 2007-01-18
how come the screensaver is all laggy? i have a new video card.

---

### Post by bodhi.zazen on 2007-01-18
1. what videocard ? monitor ?
2. did you install the proper drivers/configure X ?
3. what screensaver ?

---

### Post by SonicBOOM on 2007-01-18
how do u install the drivers for the video card on ubuntu?

---

### Post by SonicBOOM on 2007-01-18
bump

---

### Post by tronica on 2007-01-18
if you have an nVidia card here how you install those drivers

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

if you have an ATI card heres how you install those drivers

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29)

---

### Post by medley on 2007-01-18
> **bodhi.zazen said:**
> 1. what videocard ? monitor ?
2. did you install the proper drivers/configure X ?
3. what screensaver ?

You will need to enable GLX acceleration. To verify whether it is running or not, start a terminal session and type glxinfo. If it is enabled you will see a ton of info; if not it will tell you that GLX is not enabled. It almost certainly is not.

You will have to install the appropriate driver for your video card. I can't speak for ATI, but if you have an NVidia card, go to [www.albertomilone.com](www.albertomilone.com) and find his envy utility and run it. It will take care of you.

Cheers and good luck.

Medley

---

