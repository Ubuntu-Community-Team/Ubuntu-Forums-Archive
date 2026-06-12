---
title: "How do i know graphics card is working?"
date: 2007-02-26
forum: General Help
---

### Post by christoforever on 2007-02-26
So i was wondering how do i know if the cpu is being hit or the gpu when doing graphics. A few weeks ago i ran fglrxgears and the gears were spinning super fast. After uninstalling ubuntu and playing with it till no end i ran this same test yesterday and found the gears just mildly churning along.  When i type in fglrxinfo :

display: :0.0  screen: 0
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 1.5 Mesa 6.5.1

where as before it said something about ati radeon technology. Anyone have any opinions or ideas?

---

### Post by Maestro23 on 2007-02-27
The driver for your card is not installed.  Get the driver you had before and re-install it.

---

### Post by christoforever on 2007-02-27
Well i used the wiki guide to install the ati drivers. then i rebooted and still the same output for fglrxinfo. Is there something im missing?

---

### Post by Maestro23 on 2007-02-27
> **christoforever said:**
> Well i used the wiki guide to install the ati drivers. then i rebooted and still the same output for fglrxinfo. Is there something im missing?

Try the Envy script, it will be easier for you. Get the correct driver for your card and then run the script.

Envy: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

*Works for ATI and Nvidia.

---

