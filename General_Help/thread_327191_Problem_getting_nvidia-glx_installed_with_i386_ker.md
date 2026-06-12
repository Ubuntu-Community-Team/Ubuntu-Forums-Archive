---
title: "Problem getting nvidia-glx installed with i386 kernel"
date: 2006-12-28
forum: General Help
---

### Post by statictonic on 2006-12-28
I was having problem with the CPU usage spiking to 100% and then dropping and spiking again with the generic kernel, so i tried switching to i386, which solved my problem.  However I can not get the nvidia-glx drivers to work.  I tried removing them and then reinstalling them from add/remove programs, and from apt-get, it still does not work.

Is there anything additional I need to do to get them to work correctly in i386?  Right now I'm just using the nv drivers, everytime i switch to nvidia in xorg x won't load.

---

### Post by rianquinn on 2006-12-28
I would use

[HTML]http://ubuntuguide.org/wiki/Ubuntu_Edgy[/HTML]

This would show you how to install the nvidia-drivers. Typically you need to have all of the repo's enabled to be able to install the nvidia drivers because a different kernel is needed (restricted).

Rian

---

