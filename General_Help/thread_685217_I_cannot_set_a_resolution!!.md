---
title: "I cannot set a resolution!!"
date: 2008-02-02
forum: General Help
---

### Post by orasis on 2008-02-02
I have a Radeon 7000 with a TV-Output and it seems that XORG thinks that my monitor is the TV, I end up with a horribly huge resolution and massive fonts to match everytime I start X... 

Is there any way to get Xorg to stop enabling/searching/loading the TV output? ... 

I have tried everything that I know from @75 to modelines to "NoTV" and even commenting out the 'viewports 0 0", I also added and removed "MonitorLayout" "AUTO, NONE" but to no avail (and vice versa and both... @ "auto")

I know that it is something to do with this TVOUT and XORG setting my monitor as the TV for some odd reason... because I changed my video driver from "ati' and "radeon" to "vga" and sure, it was ugly, but I finally got a resolution change - same with an svga driver....

so how how how can I disable TVOUT in the generic ati/radeon driver and or XORG setup? Thanks!

---

### Post by Bubba64 on 2008-02-02
I assume you have tried resolution settings from system-preferences-screen resolution you might want to post more info otherwise such as which distribution, and system info. I am no more help than this but somebody probably can help you.

---

### Post by orasis on 2008-02-02
It is impossible to get to the screen settings - when I mean the resolution is horrible, I mean HORRIBLE - As in the menu takes up 'literally' the whole screen and fold out menus overlap each other making it impossible to do anything at all.

---

