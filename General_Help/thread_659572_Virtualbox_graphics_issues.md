---
title: "Virtualbox graphics issues"
date: 2008-01-05
forum: General Help
---

### Post by andymushu on 2008-01-05
I installed windows xp as a guest on my ubuntu gutsy host installation. XP installed fine, but when i went to run Day of Defeat: Source in steam, it brought up the loading window, then didn't bring up the actual game. Basically, the game loads, but then it displays nothing and as far as i can tell, crashes. I suspect this has something to do with virtualbox and the graphics drivers, although i haven't been able to find anything that even remotely addressing this issue. Any help would be much appreciated.

---

### Post by EndPerform on 2008-01-05
Virtualbox, as far as I know, doesn't do accelerated graphics for Windows.  Your best bet for gaming is either a Windows partition or either Cedega or Wine.

---

### Post by andymushu on 2008-01-05
Thanks for the quick reply. The whole reason for running XP in a virtual machine was to take the gaming stress off of my incompetent video card and put the strain on my more than adequate processor. If i make a windows partition, then the stress will be put back on my video card. So if there is no way to make this work in virtualbox, is there a way to utilize my excess processing power/ram for video ram, in order for me to run this in linux? I have tried wine, and i was able to run the game, except that i got a dismal 8 frames per second, average. So if there was a way to reappropriate my system ram as video ram, or something of that sort, that would be ideal. Does anyone know of something like this?

---

