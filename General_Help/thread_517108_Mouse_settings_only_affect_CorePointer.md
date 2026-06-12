---
title: "Mouse settings only affect CorePointer"
date: 2007-08-04
forum: General Help
---

### Post by wonnage on 2007-08-04
I have my xorg.conf set up so my mouse uses the evdev driver instead of mouse. Since it's a laptop and I don't have the mouse plugged in all the time, I have the touchpad set as the corepointer. In fact, X refuses to start if the mouse is set as corepointer when it's not plugged in. The corepointer autodetect also fails because it looks for the mouse driver, rather than evdev.

The problem is, I seem to get some random default sensitivity for the mouse. The settings from gnome-mouse-settings only affect the device marked as CorePointer (touchpad). Is there a way to change the sensitivity for the mouse? Here are the relevant parts of xorg.conf: 

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse" 
    InputDevice    "Synaptics Touchpad"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "ZAxisMapping" "4 5"
    Option	   "SendCoreEvents" "true"
    Option	   "Phys" "usb-0000:00:1d.1-1/input0"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option	   "CorePointer"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

```

And yes, everything aside from the sensitivity works fine. I like my back/forward buttons, but not how the mouse spazzes across the screen at the slightest touch. Thanks!

---

### Post by leif81 on 2008-05-08
I have this same problem (in Fedora 8 however). It's driving me nuts. I like my mouse nice and fast and I have no  way of adjusting the mouse speed since the CorePointer is the laptop touchpad.

---

