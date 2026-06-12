---
title: "Help!! lost high resolution!!  [Feisty+nvidia+2.6.20-14]"
date: 2007-04-07
forum: General Help
---

### Post by aymwoo on 2007-04-07
I update my PC from 6.10 to feisty....But i can't run at 1280x1024 and I'm stuck at 1024 x 768 right now.
When I scan the xorg.0.log, i found the following lines:
[COLOR="Red"](WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0): "nvidia-auto-select".
(WW) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768[/COLOR]
And the contents of xorg.conf are as follows:
> Section "Monitor"
    Identifier     "AOC 173P"
    HorizSync       30.0 - 80.0
    VertRefresh     50.0 - 75.0
    ModeLine       "1280x1024_60.00" 108.9 1280 1360 1496 1712 1024 1025 1028 1060 -hsync +vsync
    Option         "DPMS"
  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600]"
    Monitor        "AOC 173P"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection 

Any idea how to get my high resolution back? Thanks for your help!!:)

---

### Post by v0rtical on 2007-04-09
I have this same problem with Feisty...

I have a nVidia GeForce 6800 GT installed, but I can't configure it to anything above 1024x768!

help!

---

### Post by CocoAUS on 2007-04-09
You should probably just remove that entire screen section and replace it manually.  You don't need all the fancy modeline stuff.  I suggest just putting in the basics, as described [here]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution").

---

### Post by aymwoo on 2007-04-09
> **CocoAUS said:**
> You should probably just remove that entire screen section and replace it manually.  You don't need all the fancy modeline stuff.  I suggest just putting in the basics, as described [here]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution").

I have tried the way you suggest, but i failed. Could you give me  more suggestions? Thanks!!

---

### Post by v0rtical on 2007-04-10
I have also tried that and had no luck... any other ideas?

---

### Post by lawahdy on 2007-04-10
i'm stuck with that as well.. 

having Gforce 7300 and a 20" monitor.. can you Imagen how big the fonts are on the screen with the low rez.. lool.

---

### Post by laborg on 2007-04-14
I am stuck with the same problem (Geforce 6200, nvidia-glx-new).

---

### Post by black_magician on 2007-04-17
I just upgraded my monitor to a Samsung 226BW and am having the same problem.  I have an Nvidia 6800 and have tried all the tutorials I've found, but to no avail..

---

### Post by y6FgBn)~v on 2007-04-17
Was having a similar problem yesterday and ran"nvidia-settings" from terminal to alter the settings from there. It will give you the option to preview your changes to xorg.conf before you save them. You may need to run the command "sudo nvidia-settings" in order to save your changes to xorg.conf

pcybill

---

### Post by black_magician on 2007-04-17
> **pcybill said:**
> Was having a similar problem yesterday and ran"nvidia-settings" from terminal to alter the settings from there. It will give you the option to preview your changes to xorg.conf before you save them. You may need to run the command "sudo nvidia-settings" in order to save your changes to xorg.conf

pcybill

I tried that and it enabled me to go up to 1152x768.  I'm still trying to get to 1680x1050 though.

---

### Post by lawahdy on 2007-04-24
> **pcybill said:**
> Was having a similar problem yesterday and ran"nvidia-settings" from terminal to alter the settings from there. It will give you the option to preview your changes to xorg.conf before you save them. You may need to run the command "sudo nvidia-settings" in order to save your changes to xorg.conf

pcybill

this works great for me.. thanks...

---

