---
title: "Compiz ignores mouse bindings"
date: 2008-05-07
forum: General Help
---

### Post by mister_pink on 2008-05-07
I've got a Logitech marble mouse and I'd like to map the right thumb button (button 9) to move windows, rather than the default alt + LMB. I thought the easiest way to do this would be in the move plugin in compiz. However, whatever combination I set there it always uses the left mouse button. I also tried setting it in gconf editor to make sure.

Relevant bit of my xorg.conf:
```
Section "InputDevice"
        Identifier "Marble Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Buttons" "9"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "EmulateWheel" "true"
        Option "EmulateWheelTimeout" "200"
        Option "EmulateWheelButton" "8"
        Option "YAxisMapping" "4 5"
        #Option "XAxisMapping" "6 7"
EndSection
```

I think there might be some conflict with what gnome wants to do (as set in system->Preferences-> Windows) but there is no option in there to change to what I want to. A way of doing this for gnome generally would be great, as sometimes I don't use compiz.

Cheers.

---

### Post by JamonTerrell on 2008-05-07
I'm having exactly the same problem with trying to rebind resizing windows using compizconfig or gconf to edit compiz's settings.  It won't override the "mouse2" part, and if I do change the modifier keys, it causes the left mouse button to stop working until I restore it back to default.

I'm using an MX Revolution using the evdev driver.  Running Ubuntu 8.04.

---

### Post by hexeroby on 2008-08-14
I'm having the exact same problem as mister_pink.

---

### Post by bipp5 on 2008-10-21
I am also having the exact same problem.

---

