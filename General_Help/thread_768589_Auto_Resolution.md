---
title: "Auto Resolution?"
date: 2008-04-26
forum: General Help
---

### Post by damis648 on 2008-04-26
Ok i have a laptop and when i start it into ubuntu i get the login on the LPL screen so i press Fn+F8 to change to the external display, however when I change to the external display, it keeps the resolution from the laptop LPL and I have to change it manually. So heres my question (well actually I have two) but anyway: 

1. Is there a way to configure Nvidia-settings / xorg.conf so that when i plug in my external monitor it will automatically switch to it?

and 2. After switching (whether manually or if it can be done automatically), is it possible to automatically change the resolution to suite the external display?

PS. The LPL is 1680x1050 and the external display is 1900x1200

Any help would be much appreciated:)

---

### Post by damis648 on 2008-05-01
Super Bump

---

### Post by damis648 on 2008-05-01
bump

---

### Post by RAOF on 2008-05-01
> **damis648 said:**
> Ok i have a laptop and when i start it into ubuntu i get the login on the LPL screen so i press Fn+F8 to change to the external display, however when I change to the external display, it keeps the resolution from the laptop LPL and I have to change it manually. So heres my question (well actually I have two) but anyway: 

1. Is there a way to configure Nvidia-settings / xorg.conf so that when i plug in my external monitor it will automatically switch to it?
and 2. After switching (whether manually or if it can be done automatically), is it possible to automatically change the resolution to suite the external display?

PS. The LPL is 1680x1050 and the external display is 1900x1200

Any help would be much appreciated:)

I think the answers are "no" and "no", respectively :(.  For the first, I don't think the hardware signals when a new monitor is plugged in (this may be different on really new (nv5x/6x) nvidia cards), so something would need to poll the card to work out when you'd plugged a monitor in, and that tends to make the screens blink.  Not good :).

For the second, I don't really know, but none of my fiddling with the nvidia drivers has suggested a way to do this.

---

### Post by damis648 on 2008-05-02
Ok thank you anyway.

PS I know my card detects a new monitor being plugged in, as i have these same settings configured in windows.

---

### Post by mess110 on 2009-01-16
I have the same "problem"

at the moment my idea is to make a copie of x.conf in each state:
1. monitor not plugged in
2. monitor pluggged in

and then make a program that switches between them. it is really easy but I am also really lazy.. The thing is only this would not satisfy me. So I have to check how detection of monitor is checked and when it detects one it switches to one config and when it doesn't it uses the default one..

---

