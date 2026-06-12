---
title: "How to speed up mouse scrolling?"
date: 2007-11-06
forum: General Help
---

### Post by Yellowbelly on 2007-11-06
I've noticed that my windows scrolls really fast compared to this here ubuntu. I'd just like to scroll faster mainly for browsing webpages and such. Is there any way I can change to more than 3 lines per wheel click? I have a logitech mx500 if that makes any difference, and if I could enable the sidebuttons, that'd be great too.

---

### Post by fjgaude on 2007-11-06
I'm not sure if your mouse is a standard or not. If it is then you can get the side buttons to work correctly by changing your xorg.conf file. Byt the Section for "configured Mouse" and replace it like so:

```
sudo cp /etc/X11/xorg.conf /etx/X11/xorg.conf.bak

gksudo gedit /etc/X11/xorg.conf
```

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device"                "/dev/input/mice"
        Option      "Protocol"              "ExplorerPS/2"
        Option      "Emulate3Buttons"       "false"
        Option      "Buttons"               "7"
        Option      "ZAxisMapping"          "4 5"
        Option      "ButtonMapping"         "1 2 3 6 7 4 5"
EndSection
```

Highlight this section and paste the above into it.

I'm sure there is some conf file somewhere that lets you change the wheel rate, but I don't know where off the top of my head.

Such works in Firefox for back and forward.

Good luck, but do let us know how you did.

---

