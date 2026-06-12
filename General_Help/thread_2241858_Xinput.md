---
title: "Xinput"
date: 2014-08-28
forum: General Help
---

### Post by Skippy64002 on 2014-08-28
I all ready know how to use xinput to enable wheel emulation on my Logitech marble trackball where you hold down the small left button (button 8) and use the trackball to scroll up, down, left, and right. What I want to do is see if it is possible to configure it where if the left small button (button8) is pressed it scrolls down with out the need to use the track ball, and if the right small button is pressed (button 9) it scrolls up. I have examined many posts, the xinput --help, man page, and other articles on the net and have not been able to understand things enough to make this happens. right when I think I have figure out one the commands syntax i find out I that I didn't really understand it.

FOR EXAMPLE
```
xinput set-int-prop "Logitech USB Trackball" "Evdev Wheel Emulation Axes" 8 6 7 4 5
```

From the man page the first number near the end is the format witch can be 8, 16, or 32. What is the "format" and why does it need to be 8, 16 , or 32? The documentaion is very light regarding this portion of the syntax.

Also looking at examples from other posts regarding wheel emulation, using the "Edev Wheel Emulation *" options might not be the ones that I want to you use to achive my intended goals. As it appears to set the emulation to a button that is pressed, held, and then the trackball moved in the appropriate direction. since I want the scroll feature to go up when the button is pressed witch option would I need to set to have this happen? my reason for doing this is that i rarley have the need to scroll right and left, mainly just up and down. It would be quicker for me to just press the appropriate mouse button to scroll up and down as I did when I had Windows installed. So any help would be greatly appriciated! For reference here is the output from xinput list-props and my button maps  so you can see witch available properties it has.

[HR][/HR]xinput get-button-map 8
1 2 3 4 5 6 7 8 9

xinput list-props 8
Device 'Logitech USB Trackball':
    Device Enabled (141):    1
    Coordinate Transformation Matrix (143):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (263):    0
    Device Accel Constant Deceleration (264):    1.000000
    Device Accel Adaptive Deceleration (265):    1.000000
    Device Accel Velocity Scaling (266):    10.000000
    Device Product ID (257):    1133, 50184
    Device Node (258):    "/dev/input/event3"
    Evdev Axis Inversion (267):    0, 0
    Evdev Axes Swap (269):    0
    Axis Labels (270):    "Rel X" (151), "Rel Y" (152)
    Button Labels (271):    "Button Left" (144), "Button Middle" (145), "Button Right" (146), "Button Wheel Up" (147), "Button Wheel Down" (148), "Button Horiz Wheel Left" (149), "Button Horiz Wheel Right" (150), "Button Side" (261), "Button Extra" (262)
    Evdev Middle Button Emulation (272):    0
    Evdev Middle Button Timeout (273):    50
    Evdev Third Button Emulation (274):    0
    Evdev Third Button Emulation Timeout (275):    1000
    Evdev Third Button Emulation Button (276):    3
    Evdev Third Button Emulation Threshold (277):    20
    Evdev Wheel Emulation (278):    1
    Evdev Wheel Emulation Axes (279):    6, 7, 4, 5
    Evdev Wheel Emulation Inertia (280):    10
    Evdev Wheel Emulation Timeout (281):    200
    Evdev Wheel Emulation Button (282):    8
    Evdev Drag Lock Buttons (283):    0
    Evdev Wheel Emulation X Axis (545):    6
    Button Wheel Up (147):    9

[HR][/HR]

---

