---
title: "mouse/keyboard delay"
date: 2008-04-30
forum: General Help
---

### Post by EXetoC on 2008-04-30
Hello!

I get massive mouse/keyboard delay in an OpenGL game called "Urban Terror" when i move the mouse/mousewheel rapidly, and it goes away as soon as i stop doing things rapidly (well after it has processed every registered input, wich could take a while depending on how fast and for how long i scroll or move the mouse rapidly). I'm using Hardy Heron currently, and the same thing happened a month ago when i used Gutsy Gibbon. I did fix this on Gutsy somehow but i can't remember how.

This is what the mouse section looks like in "/etc/X11/xorg.conf":
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "SampleRate" "100"
    Option         "Resolution" "1000"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "auto"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection

Does anyone have any idea about what may cause this issue and does anyone know how to fix it?

---

### Post by EXetoC on 2008-04-30
Someone said that the port polling rate may be too low or something like that. I've also tried to recreate the bug in another game called Teeworlds, but without result.

---

### Post by EXetoC on 2008-05-01
Problem solved.

The solution was to enter this in the terminal:
"export SDL_VIDEO_X11_DGAMOUSE=0"

---

