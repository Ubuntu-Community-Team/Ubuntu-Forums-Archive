---
title: "gutsy refresh rate @ 50hz - 1280x800, can i get 60?"
date: 2007-11-13
forum: General Help
---

### Post by bishop9226 on 2007-11-13
> Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option          "metamodes" "1920x1200_60 +0+0
EndSection



can i get it to 60? i made xorg.conf say the above and its still locked in at 50 on 1280x800

using e1505 dell with the geforce go 7300 as you can see

thx

---

### Post by laceiba on 2007-11-14
Does it look bad at 50 Hz? Vertical refresh rates don't matter very much with LCDs. CRTs on the other hand need fast refreshes in order to look good.

---

### Post by MightyMe on 2007-11-17
I posted something on the same issue. If you start "nvidia-settings" from the command prompt, does that one still say 50Hz? For me it says 60Hz, while in screen resolution under Preferences says 50Hz.

I can pick 50 or 51 Hz for my monitor IQT L70S in screen resolution, but nvidia-settings says 60 or 75 Hz.....strange.

In other words, 50Hz may very well be 60 Hz...?! Dont really know which one to trust.

I have a GeForce 7600GS and the restricted device driver enabled. Sorry for the added confusion, but you may already be running it on 60Hz....?

---

### Post by brad1138 on 2007-11-17
> If you start "nvidia-settings" from the command prompt, does that one still say 50Hz? For me it says 60Hz, while in screen resolution under Preferences says 50Hz.


I have noticed the same thing, you need to run "nvidia-settings" from terminal and you will have all the settings you need. For me the "Screen resolution" setting gives me very few options. I usually create a launcher for nvidia-settings.

---

