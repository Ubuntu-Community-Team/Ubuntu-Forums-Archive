---
title: "Middle mouse button not working with new mouse"
date: 2007-05-25
forum: General Help
---

### Post by ahawks on 2007-05-25
I just upgraded to a new mouse at work, which has the usual left/right click, mouse wheel/middle button, as well as 2 extra buttons.  It's a cheap-o HP mouse. 

In Redhat Enterprise 4, the mouse works as expected. Middle click = middle click, extra 2 buttons are ignored. 
In Ubuntu, the middle click isn't recognized, but is bound to one of the 2 additional buttons.

I've compared xorg.confs, and they are identical. 
I've tried several different drivers for the mouse.

To be clear: I really don't care about the extra 2 buttons, I just want my middle click back as the middle button :) 

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "IMPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "Emulate3Buttons"       "false"
EndSection

```

Are there any config files other than xorg.conf that might be responsible for this?

Edit: here's a link to the mouse. [http://www.amazon.com/Optical-Five-Button-Light-Up-Scroll-HEWP2352AA/dp/B000E7A5UE](http://www.amazon.com/Optical-Five-Button-Light-Up-Scroll-HEWP2352AA/dp/B000E7A5UE)

---

### Post by mbradlcu on 2007-05-25
here's my xorg.conf  section,, I'm not sure if no=false but drop it in and see if it works.. good luck

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

---

### Post by ahawks on 2007-05-25
No luck, but thanks.

To clarify: The root of the issue looks like there aren't even any events being thrown from a middle click.

The mouse has physical buttons:
Left, scroll wheel/middle button, right
extra1
extra2

xev recognizes the following mapping:
left: button 1
middle click: (no event shows up)
right: button 3
scroll up: button 4
scroll down: button 5
extra1: button2
extra2: (no event shows up)

I've tried every mouse protocol I can think of: intellimouse, im/ps2, auto, ps2, ...

Again, RHEL4 picks this up just fine and behaves as any other normal wheel mouse. Ubuntu refuses to recognize middle click as button 2.

---

### Post by tedrogers on 2007-07-04
I have the same problem with my PS2 mouse, the only difference being that I am using a USB adapter into the PS2 port.

Just like you, xev only gives output for the regular left and right buttons (and movement), but nothing for wheel up/down or wheel click.

I really want my wheel scroll and click!

I would normally use the mouse in the USB port where it works fine, but as my laptop only has one USB port and I want to use this for a USB drive, I'd really like to free it up permanently and use my USB mouse with the adapter in the PS2 port.

Maybe the PS2 port just can recognise the missing functions?

Any ideas anyone?

---

### Post by Ayuthia on 2007-07-04
Here is a link to the mouse documentation on [www.x.org](www.x.org).  Check the link in the Supported Hardware section.  Hopefully this will give you the information that you need to get scrolling to work.

[http://www.x.org/archive/X11R6.8.2/doc/mouse.4.html](http://www.x.org/archive/X11R6.8.2/doc/mouse.4.html)

---

