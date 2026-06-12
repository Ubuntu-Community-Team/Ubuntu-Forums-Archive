---
title: "Synaptic removes GUI packages"
date: 2007-01-22
forum: General Help
---

### Post by siddharth.dawara on 2007-01-22
Hi, I'm using Xubuntu and whenever I use Synaptic to upgrade my Firefox install or try to install some GUI like the MySQL Query Browser Synaptic tries to remove the following packages:

1. xwindow-system-core
2. xserver-xorg
3. xubuntu-desktop

When I remove these packages and restart my PC the XCFE GUI is gone, I tried restoring the packages using the shell apt-get but it didn't work. I had to re-install Xubuntu.

I was hoping there's a way to fix this, because I'm missing out on quite a bit. 

Thanks,
Sid.

---

### Post by siddharth.dawara on 2007-02-08
Instead of copying the sources.list from the Ubuntu Dapper Drake guide, I enabled them through Applications>System>Software Properties.

Now, nothing tries to remove xserver-xorg :D
Cheers!

---

