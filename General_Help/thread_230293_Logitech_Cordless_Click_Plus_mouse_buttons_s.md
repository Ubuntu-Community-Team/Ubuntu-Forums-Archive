---
title: "Logitech Cordless Click Plus mouse buttons :s"
date: 2006-08-05
forum: General Help
---

### Post by PingunZ on 2006-08-05
I can't get my Logitech Cordless Click Plus mouse working.
I just want the back and forwards buttons to work !!
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ZAxisMapping" "4 5"
EndSection

```
I changed the ZAxisMapping to "6 7" but then the my scroll didnt work.
Plz help me !!

---

### Post by Saibot on 2006-08-06
Well I have the Logitech MX1000 mouse so I can't guarantee this will work with yours, but it's worth a shot.  I tried to go through a how-to to get them all working and almost borked my system.  I really wasn't all that concerned with getting EVERY button working - but the lack of a back button was killing me.  Then someone posted this little gem and it got back, forward, cruise down, and mouse wheel working.  The only buttons that don't do what they are supposed to do are cruise up, side scrolling, and application switch.  Who cares!  I'm just tickled to get back and forward working!  One of my other systems has a simpler logitech mouse with just a wheel and back button - this gave it full functionality.

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection
```

---

### Post by PingunZ on 2006-08-06
Works great, thank you !

---

### Post by Bloodbath on 2006-08-07
That made my side buttons work, thanks!
I think Ubuntu is now my primary OS.

---

### Post by sunexplodes on 2006-11-13
It worked for me, too. Until I logged out. When I logged back in, the thumb button didn't work anymore.

Anybody know why this would be? I've doublechecked the xorg.conf file and the changes I made are still there.

---

### Post by kibmcz on 2006-11-14
Worked great on my Cordless Click Plus too... Great work... I was lost without those buttons.

---

### Post by sunexplodes on 2006-11-16
Hey, I hate to be the annoying thread-bumper, but this is weird. The above-mentioned fix worked for me for ONE session and then crapped out as soon as I logged out and then back in.

The changes I made to xorg.conf are still there, does anybody have a clue?

---

