---
title: "Kubuntu Feisty XGL Shutdown button"
date: 2007-04-13
forum: General Help
---

### Post by ponkarthik on 2007-04-13
Hi all,

  I installed Feisty/ Kubuntu on my Dell Inspiron 6400. Now I am running beryl successfully using XGL as my ATi Radeon X1300 doesnt support AIGLX.

I am not able to get the shutdown / reboot button directly from Beryl session. I tried

```

 #! /bin/sh
 Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer -dpi 96 &
 sleep 4  
 export DISPLAY=:1 
 
 cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
 xauth -i add :1 . "$cookie"
 exec startkde


```

for my startxgl.sh.

But it does not work for me as I am running KDM .

Is there anyway to get the restart/shutdown buttons for KDE users running KDM ?

Thanks

Karthik

---

### Post by s0undt3ch on 2007-04-23
I'm facing the same problem, and I also can't seem to simply logout. I have to restart kdm everytime. :(

---

