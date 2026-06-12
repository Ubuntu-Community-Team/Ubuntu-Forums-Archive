---
title: "permanently reduce mouse pointer speed"
date: 2013-11-02
forum: General Help
---

### Post by macakcira on 2013-11-02
I have a mouse that works fine under Windows, but under Ubuntu it flies like crazy and I have a hard time controlling it. So I googled how to slow down mouse pointer in Ubuntu and found this code 

xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Accel Constant Deceleration" 1.5

where "SynPS/2 Synaptics TouchPad" is name of the mouse and 1.5 is value of deceleration.

And it works fine until I restart the system and the mouse is back at its original speed. Is there a way to permanently change mouse speed so I don't have to type the code over and over again? Thanks!

---

### Post by philinux on 2013-11-02
> **macakcira said:**
> I have a mouse that works fine under Windows, but under Ubuntu it flies like crazy and I have a hard time controlling it. So I googled how to slow down mouse pointer in Ubuntu and found this code 

xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Accel Constant Deceleration" 1.5

where "SynPS/2 Synaptics TouchPad" is name of the mouse and 1.5 is value of deceleration.

And it works fine until I restart the system and the mouse is back at its original speed. Is there a way to permanently change mouse speed so I don't have to type the code over and over again? Thanks!

Top right on desktop. Click the gear and choose system settings then Mouse.

---

### Post by macakcira on 2013-11-02
Hey thanks for pointing me to that system settings I didn't know existed (new with Linux). I tried it and while it does slow down my cursor, it doesn't slow it enough, even if I put it to the minimum (you probably now get the point how fast it is). Maybe if I can somehow increase the range of how much it slows down the cursor or something.

Btw, I found this solution, but I don't have xorg.conf file in X11 folder...

[INDENT=2]
[/INDENT]
[INDENT]To make the config persistent *(and make it system wide)*, you will need to edit your xorg.conf (/etc/X11/xorg.conf).
[/INDENT]
[INDENT]Section "InputClass"
   Identifier      "Razer"                    # Whatever you want.
   MatchProduct    "Razer Razer DeathAdder"   # Product name from xinput list.
   Option          "ConstantDeceleration" "3" # The same value as xinput.
EndSection
  Once you reboot, you should have the same result as the xinput command.
[/INDENT]

---

