---
title: "Americas Army Help"
date: 2006-07-18
forum: General Help
---

### Post by epidemik on 2006-07-18
When i try to run americas army i get an error.

> kate@kate:~$ sudo sh /usr/local/games/armyops/armyops
Password:
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error
kate@kate:~$

What is happening and how do i fix it?

---

### Post by meng on 2006-07-18
I suspect it would help to know your graphics card and which driver is being used. Have you successfully run any other 3d graphics games/applications with your setup?

---

### Post by epidemik on 2006-07-18
Lol. i got the whole system in ga garage sale for 30 bucks but i think it meets the minimum recuirements. Im not sure about the graphics card.
> 
0000:01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)


and i havent played other games

---

### Post by meng on 2006-07-18
Try installing nvidia-glx from repositories and see if that works. Vanta is a fairly old card, correct? Possibly considered legacy ...

---

