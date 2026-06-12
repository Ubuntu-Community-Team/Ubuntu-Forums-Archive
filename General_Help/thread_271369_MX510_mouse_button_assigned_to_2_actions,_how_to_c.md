---
title: "MX510 mouse button assigned to 2 actions, how to change it to 1?"
date: 2006-10-04
forum: General Help
---

### Post by Tauceti38 on 2006-10-04
I recently purchased a mx510 mouse to replace my old one, and am working on getting all of the buttons working. I used [this]("http://ubuntuforums.org/showthread.php?t=219894&highlight=setup+mouse+buttons") very helpful tutorial and got most everything working, but for some reason the scroll up and scroll down buttons (the actual button, not the wheel) appear to be assigned to multiple actions.

I can test those buttons in xev, and get the following output (and yes, all of this came from a single button press):

Scroll up button
```

ButtonPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x2c00002, time 350282656, (34,46), root:(1992,95),
    state 0x0, button 9, same_screen YES

EnterNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x0, time 350282656, (34,46), root:(1992,95),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  68  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x2c00002, time 350282656, (34,46), root:(1992,95),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x2c00002, time 350282656, (34,46), root:(1992,95),
    state 0x800, button 4, same_screen YES

LeaveNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x0, time 350282656, (34,46), root:(1992,95),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

ButtonRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x2c00002, time 350282800, (34,46), root:(1992,95),
    state 0x0, button 9, same_screen YES
```

Scroll down button
```
ButtonPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x2c00002, time 350408851, (21,31), root:(1979,80),
    state 0x0, button 10, same_screen YES

EnterNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x0, time 350408851, (21,31), root:(1979,80),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus NO, state 0

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  23  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x2c00002, time 350408851, (21,31), root:(1979,80),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x2c00002, time 350408851, (21,31), root:(1979,80),
    state 0x1000, button 5, same_screen YES

LeaveNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x0, time 350408851, (21,31), root:(1979,80),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus NO, state 0

ButtonRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x117, subw 0x2c00002, time 350409035, (21,31), root:(1979,80),
    state 0x0, button 10, same_screen YES
```

From this output, it appears that these buttons are assigned to button 9 and 4 for the scroll up button, and button 10 and 5 for the scroll down button. Unfortunatly with this setup, I can't map actions to these buttons, other than the same actions mapped to the scroll wheel. Unless I can fix this, I essentially have a normal 5 button mouse, which more or less defeats the purpose of the mx510, for me at least.

Any help would be greatly appreciated, thanks.

---

### Post by aidanr on 2006-10-04
i have the 510 aswell, it works fine for me in games, i can use all the buttons, for filebrowsing and webbrowsing the side buttons don't go back/forward between pages but i don't mind that, everything else works the way it should and i can bind the side buttons to actions, this is my xorg.conf mouse section

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "Resolution" "800"
EndSection

btw, i'm using the usb, not with the ps2 adapter

---

### Post by jakster on 2006-10-17
judging from the howto here

[http://ubuntuforums.org/showthread.php?t=219894&highlight=setup+mouse+buttons](http://ubuntuforums.org/showthread.php?t=219894&highlight=setup+mouse+buttons)

you can use a tool called lomoco (in edgy/universe)

With lomoco you can do

lomoco --no-sms 

Then your mouse will only send 9 & 10 events.

---

