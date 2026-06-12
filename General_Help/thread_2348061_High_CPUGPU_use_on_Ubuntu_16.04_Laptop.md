---
title: "High CPU/GPU use on Ubuntu 16.04 Laptop"
date: 2016-12-31
forum: General Help
---

### Post by akatsuk on 2016-12-31
I have a MSI GE72 Apache running with Ubuntu 16.04. Since a  few days I've noticed that the CPU (Intel I5 4210H) usage is getting  really high on top or htop (more than 300%) when playing games, even  ones who doesn't require a powerful system.
I first thought that it  was because the game was using the "integrated" intel GPU, and not my  Nvidia GTX960M, but all the settings and priorities are on the Nvidia  GPU, and the GPU utilization is also going super high, sometime 99% in  nivdia-settings while playing a game.

I've read a lot of post in a  lot of forums, tried some solutions : prime select Nvidia, update  Nvidia drivers, OpenGL drivers, check with **dpkg -l | grep vdpau** and **glxinfo | grep render, **everything is ok. I really don't know what to try next, the memory use seem to be normal.

It  seems that there's something that causes all of this but I'm really  missing something, I've used Ubuntu only for a few months.

Any suggestions ? 

Thanks

Edit : My CPU% while I'm not doing anything is normal, around 2-3%

---

