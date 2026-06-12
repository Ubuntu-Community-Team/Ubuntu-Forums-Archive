---
title: "btnx - old buttons still there (double mapping?)"
date: 2008-01-11
forum: General Help
---

### Post by phillips321 on 2008-01-11
Hi guys,

BTNX = so far so good other than one problem.

I have 2 thumb buttons (buttons 6 & 7), i have mapped these to Ctrl+Alt+Left and Ctrl+Alt+right using BTNX. This works fine.

But, what i do notice is that the buttons still also represent what the buttons were originally automatically mapped to (Middle click and right mouse), thus this can cause some very wierd problems.

Any idea how to prevent this?

Cheers

Section from xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

---

### Post by phillips321 on 2008-01-11
bobs your uncle, it's now fixed!

What i had to do was change the section protocol to** auto**

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      **"auto"**
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

---

