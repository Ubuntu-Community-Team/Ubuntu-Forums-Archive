---
title: "Invert Mouse (Trackball) Axis"
date: 2018-10-22
forum: General Help
---

### Post by clalian on 2018-10-22
Hello,
I use my mouse with the horizontal (left-right) axis inverted.
I had 16.04 installed, and I ran at startup:
```
xinput set-prop 9 "Evdev Axis Inversion" 1, 0
```

Yet I upgraded to 18.04, and that command no longer works.

So I listed my input devices with
```
xinput
```

That gave me the ID of the Kensington trackball I use, which is ID=9.
I then checked the properties for, and the output is below:
```
[~]$ xinput --list-props 9
Device 'Kensington      Kensington Expert Mouse':
        Device Enabled (140):   1
        Coordinate Transformation Matrix (142): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        libinput Natural Scrolling Enabled (277):       0
        libinput Natural Scrolling Enabled Default (278):       0
        libinput Scroll Methods Available (279):        0, 0, 1
        libinput Scroll Method Enabled (280):   0, 0, 0
        libinput Scroll Method Enabled Default (281):   0, 0, 0
        libinput Button Scrolling Button (282): 2
        libinput Button Scrolling Button Default (283): 2
        libinput Middle Emulation Enabled (284):        0
        libinput Middle Emulation Enabled Default (285):        0
        libinput Accel Speed (286):     0.000000
        libinput Accel Speed Default (287):     0.000000
        libinput Accel Profiles Available (288):        1, 1
        libinput Accel Profile Enabled (289):   1, 0
        libinput Accel Profile Enabled Default (290):   1, 0
        libinput Left Handed Enabled (291):     0
        libinput Left Handed Enabled Default (292):     0
        libinput Send Events Modes Available (262):     1, 0
        libinput Send Events Mode Enabled (263):        0, 0
        libinput Send Events Mode Enabled Default (264):        0, 0
        Device Node (265):      "/dev/input/event3"
        Device Product ID (266):        1149, 4128
        libinput Drag Lock Buttons (293):       <no items>
        libinput Horizontal Scroll Enabled (294):       1
```

What could I run to have the cursor flip once again horizontally (left-right)?

I am lost as to what to do.
I am trying:
```
$xinput --set-prop 9 ??????
```

What would go in there?

Thank you!

---

### Post by clalian on 2018-10-22
Got it!
On my specific case, with the above information (and device), the command was:
```
xinput --set-prop 9 142 -1 0 0 0 1 0 0 0 1
```

---

