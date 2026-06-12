---
title: "Why does my Logitech video camera have the light on??"
date: 2021-07-20
forum: General Help
---

### Post by david503 on 2021-07-20
Why does my Logitech video camera have the light on??


It's a little green light on the upper right side. WHY??  If I put my hand over it the light turns off.

WHY is the camera light on????????????????

Even if I shut down all applications the light is still on???????????

Oh 18.04
 Distributor ID:	UbuntuDescription:	Ubuntu 18.04.5 LTS
Release:	18.04
Codename:	bionic

---

### Post by TheFu on 2021-07-20
Updated: My Logitech C920 webcam shows 2 blue curved LEDs on each side when used by a program.  Some only enable the LEDs when it is actually grabbing images/video (chromium is like this) and others show the LEDs all-the-time (guvcview), which I suppose means the program is grabbing video always.

Is yours fancy, perhaps with autofocus or IR?  It is from 2015-ish.
I don't leave the webcam connected. It is only connected when joining a video call. Common sense security.

**v4l2-ctl -l** will show the possible settings. I routinely set the zoom and brightness this way for consistency.  I don't see any LED controls in the list of options. Example cmds:
```
v4l2-ctl -d /dev/video0 -c zoom_absolute=200
v4l2-ctl -d /dev/video0 -c brightness=100
```

---

### Post by Impavidus on 2021-07-20
Have you checked the manual of your camera? Ubuntu may not even be aware of the existence of that green led.

---

### Post by Autodave on 2021-07-20
Mine has a green light that is on whenever a program like Cheese or guvcview or OBS is using it.  However, when the program is closed the light goes off.

---

### Post by ajgreeny on 2021-07-20
And mine, which is an old (12 yrs) Logitech of unknown model number, but without microphone, is just like Autodave's, showing a light only when actively working.

---

