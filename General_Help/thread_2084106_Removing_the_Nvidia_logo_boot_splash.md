---
title: "Removing the Nvidia logo boot splash?"
date: 2012-11-14
forum: General Help
---

### Post by ojdon on 2012-11-14
Hi there, on my Ubuntu 12.10 installation I'm using the Proprietary driver ready for when Steam comes out of the "invite only" stage. When I boot Plymouth displays the nice Ubuntu splash at the correct resolution but it has a Nvidia logo flash on for a second, just wondering if I can turn this boot splash off and just have the Ubuntu Plymouth Splash?

Thanks!

---

### Post by ojdon on 2012-11-15
Anyone?

---

### Post by mag1strate on 2012-11-15
Apparently, there are numerous more options for xorg.conf files than I had previously known. One of them is specific to your situation. If you look at the Third option down ("option nologo"). You should be able to disable it that way:

[http://us.download.nvidia.com/XFree86/Linux-x86/302.17/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86/302.17/README/xconfigoptions.html)

---

