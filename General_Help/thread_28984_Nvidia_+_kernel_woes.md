---
title: "Nvidia + kernel woes"
date: 2005-04-22
forum: General Help
---

### Post by Juneau on 2005-04-22
Hey everyone,

I've got the default 386 kernel installed with nvidia drivers installed.

But every now and then the computer locks up, you can move the mouse but everthing else becomes unresponsive. 

I believe this is due to the nvidia drivers because in xorg.conf I changed the driver to NV instead of NVIDIA and the problem went away.

Any tips on how to stop this problem?

Also I would like to istall a new kernel (i686) but when I do nvidia stops working. I tried uninstalling then installing the nvidia drivers after the new kernel is installed but this does'nt work.

Thanks in Advance!

---

### Post by PMO6022 on 2005-04-22
It seems that a lot of people are having this problem: see [http://ubuntuforums.org/showthread.php?t=24279]("http://ubuntuforums.org/showthread.php?t=24279")

After reading the link, I disabled RenderAccel, and I haven't seen the problem since.

---

