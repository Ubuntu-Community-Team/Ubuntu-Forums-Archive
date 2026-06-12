---
title: "Fiesty Mouse issue: CLI workaround?"
date: 2007-04-28
forum: General Help
---

### Post by wog on 2007-04-28
The original problem: The Accelleration slider in System -> Preferences -> Mouse under the Motion tab is permanently set on Slow. Moving the slider does not alter the behavior of the mouse.

Since the Acceleration slider control for the mouse does not seem to function anymore, and since I am not a programmer, and can therefore not check the code myself, what is it that those controls are actually supposed to do? Is there something I can change with gedit or pico to make the mouse work the way it has in previous versions?

And what do I do then, to make the system recognize the files have been altered?

---

### Post by dcstar on 2007-04-29
> **wog said:**
> The original problem: The Accelleration slider in System -> Preferences -> Mouse under the Motion tab is permanently set on Slow. Moving the slider does not alter the behavior of the mouse.

Since the Acceleration slider control for the mouse does not seem to function anymore, and since I am not a programmer, and can therefore not check the code myself, what is it that those controls are actually supposed to do? Is there something I can change with gedit or pico to make the mouse work the way it has in previous versions?

And what do I do then, to make the system recognize the files have been altered?

Check your /etc/X11/xorg.conf file and make sure your mouse/pointer settings are correct.

---

### Post by wog on 2007-04-29
> **dcstar said:**
> Check your /etc/X11/xorg.conf file and make sure your mouse/pointer settings are correct.

xorg.conf contains this:
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

The actual mouse I have is a Microsoft USB Optical Mouse. The kind with a roller in the middle that doubles as a button. 

Is the above and what I have a match? I can't tell from what xorg.conf says.

---

