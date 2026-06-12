---
title: "All I get is wallpaper and mouse cursor on the screen"
date: 2013-12-08
forum: General Help
---

### Post by tom14 on 2013-12-08
I've installed Ubuntu 13.10,everything was going without any problem,but now,after I start the pc,and after login,I get only wallpaper and mouse cursor.I can open the terminal though.I tried unity --reset,but I get message:"the reset option is now deprecated".I don't know what to do now...

---

### Post by electrohandyman501 on 2013-12-08
Can you see the information bar at the top of the screen?
If you press and hold the "windows" or as linux calls it the "super" key, can you see the HUD display? 
It almost sounds like a display setting issue. I had a similar situation with a VMWare install, but I can't remember exactly what I did to fix it.........#-o
With the super key you can tap it and bring up the Dash Home screen where you can open system settings.(you can also probably open it thru the terminal command line, I'm not that fluent with command line yet to tell you what to type.....)

---

### Post by tom14 on 2013-12-12
> **electrohandyman501 said:**
> Can you see the information bar at the top of the screen?
If you press and hold the "windows" or as linux calls it the "super" key, can you see the HUD display? 
It almost sounds like a display setting issue. I had a similar situation with a VMWare install, but I can't remember exactly what I did to fix it.........#-o
With the super key you can tap it and bring up the Dash Home screen where you can open system settings.(you can also probably open it thru the terminal command line, I'm not that fluent with command line yet to tell you what to type.....)
Thank you electrohandyman501.I've tried everything,but no success,nothing but background.So what I did,I installed xubuntu 12.04 which works just fine.I guess my machines are just too old to accept any other or better kind of ubuntu,so I'll have to use xubuntu for a while.Thanks for your help...

---

### Post by Frogs Hair on 2013-12-12
The Unity reset command changed in 12.10  . 
```
setsid unity
```Reset Compiz 
```
dconf reset -f /org/compiz/
```

---

