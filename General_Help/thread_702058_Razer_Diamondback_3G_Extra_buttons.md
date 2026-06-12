---
title: "Razer Diamondback 3G: Extra buttons?"
date: 2008-02-19
forum: General Help
---

### Post by pxc on 2008-02-19
Yeah, I've read the other threads (or at least many of them. None of them (I think) specifically mention the Diamondback 3G. I tried their solutions, anyway.

My extra buttons don't work. I have four extra buttons (two on each side). The two buttons on the left side mimic a middle click, and xev tells me no difference between the two. The top-right button emulates a right click, and the bottom right also a middle click. When I change my xorg.conf mappings to switch so it's
```
Option "ButtonMapping" "2 1 3 4 5 6 7 8 9"
``` it interestingly switches the roles of the side-buttons as well.

Halp?

---

### Post by allenb on 2008-02-20
Here's the section of my xorg.conf for my Razer Diamondback 3G:
```
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Resolution" "1600"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mice"
    Option         "Name" "Razer Diamondback3G Optical Mouse"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

I don't even try to map all 9 buttons anymore, was having too many problems trying to get that to work.  Strange thing is, my button behavior changes without altering my xorg.conf.  That is, the side buttons that handle back/forward in a web browser now might not be the same ones that handle that function next time I boot (the regular buttons and scroll wheel don't have this problem, just the side buttons).  This may be a side effect of listing a 9-button mouse as a 7-button mouse, I'm not sure.  Playing games through Wine doesn't have this problem, all buttons are consistently and correctly detected.

HTH

---

### Post by allenb on 2008-02-20
From reading other Razer Diamondback threads on this forum, I have also discovered this:

```
sudo xmodmap -e "pointer = 1 2 3 4 5 6 7"
```

Running that in a terminal inside X (using the config shown above) gives me the expected behavior for the right- and left-click buttons, scroll wheel, and left side buttons (back/forward).  The two right-side buttons mimic the scroll wheel at the moment.

---

### Post by 1veedo on 2008-07-15
Any idea how to set up on-the-fly sensitivity control?  I bought it thinking this was controlled on the hardware level.  You're supposed to be able to hold button three (top left) and use the scroll wheel to change the dpi.

---

