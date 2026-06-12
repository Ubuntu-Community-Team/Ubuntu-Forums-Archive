---
title: "Screensaver problem..."
date: 2007-10-22
forum: General Help
---

### Post by Slartibartfast on 2007-10-22
Hello all! 

I have a pretty weird problem. 

I've turned off the screen saver in System > Properties > Screensaver, and turned off Power Management, but still the screen goes black after about 20 minutes when i watch a movie in for example VLC or Mplayer... Do i have to remove thescreen saver totally, or does anyone know how to fix this?

Any help is highly appreciated!

Thanks in advance! :)

//Slartibartfast

---

### Post by Slartibartfast on 2007-10-22
I just uninstalled the whole gnome-screensaver thing.. still have the same problem :(
This is getting on my nervers. Does anyone have a solution to this?

---

### Post by dayvy on 2007-10-22
Have you checked the power management options in your bios?

---

### Post by josephu on 2007-10-22
I have the same problem as well. 
I shut off the screensaver and disabled power management. Yet if PC is idle for over 5 minutes the sceen blanks out. 
It's not a BIOS issue (I checked). I'm going to check if it's compiz related by closing compiz and checking if this happens.

---

### Post by marianoi on 2007-10-22
Exact same problem here. Dell Latitude 505...

---

### Post by ssd008 on 2007-10-22
I have the exact same problem on my tower.

---

### Post by josephu on 2007-10-22
OK, here's my new status:
I started a new session **without** running xgl, compiz, gnome-power-manager. 
I left the PC with a timer running and after 5 minutes the screen blanked off. I would really like to understand what's going on. Is it X itself?
I can't keep playing right now, I'll look into xorg.conf tomorrow.

---

### Post by Slartibartfast on 2007-10-23
I think I've found a fix, or it was in the latest set of updates, not shure wich one :P

from the thread @ [http://ubuntuforums.org/showthread.php?t=585353&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=585353&highlight=screensaver)

> **tim__b said:**
> It seems that the options ```
Option "DPMS"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
```in xorg.conf in the section ServerLayout help to keep the monitor alive. never the less gnome-power-preferences settings are still ignored for me.

i put that in my xorg.conf, and since then, i can watch videos without the screen getting black :) YAY!

---

### Post by josephu on 2007-10-26
I edited xorg.conf in the same way and it solved the problem for me too.
Thanks.

---

