---
title: "Trying to add a custom resolution - X Error of failed request"
date: 2021-10-12
forum: General Help
---

### Post by lyicx on 2021-10-12
hello there. im trying to add a custom resolution (1600x900) but for some reason despite following guides on how to, i just get this error and i have no clue on how to get past this

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32

```

the commands i've been doing aswell are

> 
cvt 1600 900 

> 
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

> 
xrandr --addmode HDMI-0 "1600x900_60.00" 


its worth noting i am running on Ubuntu Budgie 20.04.3 LTS with a NVIDIA GTX1650 running the latest proprietary drivers (470) and i want to add this resolution so applications (games) can recognise 1600x900 as an actual resolution because thats just how i do play my games with windowed mode and some require dodgy configuration tweaks in the game and that

---

