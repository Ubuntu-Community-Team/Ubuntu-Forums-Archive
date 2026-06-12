---
title: "Cursor randomly jumping to trash icon"
date: 2014-09-21
forum: General Help
---

### Post by Tornikee on 2014-09-21
(I searched for similar threads but found nothing)

Since installing 14.04 my mouse cursor has been randomly jumping to the trash icon in launcher while I'm typing/clicking/etc. This is not related to my laptop's touchpad, as I have tried selecting *disable while typing* setting but to no effect.

Anybody having similar issue?

---

### Post by xc3RnbFO8P on 2014-09-21
I have this issue with my Lenovo. The mousepad is very sensitive for finger fat (when eating snacks).
Have you  tried to clean the mousepad,
Or does your laptop have touchscreen?

---

### Post by Tornikee on 2014-09-21
Thanks for the reply. Haven't tried cleaning the pad, but I doubt it's because of finger fat -- it only happens with irregular intervals of 30mins or longer.

---

### Post by xc3RnbFO8P on 2014-09-21
Show the output of:
> xinput

[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

---

### Post by Tornikee on 2014-09-21
Here you go

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=10    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]
```

---

### Post by xc3RnbFO8P on 2014-09-22
Now you have to do 2 things open terminal 1 and run:
> xinput --test 13
then open terminal 2:
> xinput --watch-props 13
and show output of terminal 2

---

### Post by Tornikee on 2014-09-22
Here it is

```
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (135):    1
    Coordinate Transformation Matrix (137):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (258):    1
    Device Accel Constant Deceleration (259):    2.500000
    Device Accel Adaptive Deceleration (260):    1.000000
    Device Accel Velocity Scaling (261):    12.500000
    Synaptics Edges (262):    1765, 5369, 1635, 4429
    Synaptics Finger (263):    25, 30, 0
    Synaptics Tap Time (264):    180
    Synaptics Tap Move (265):    233
    Synaptics Tap Durations (266):    180, 180, 100
    Synaptics ClickPad (267):    1
    Synaptics Middle Button Timeout (268):    0
    Synaptics Two-Finger Pressure (269):    282
    Synaptics Two-Finger Width (270):    7
    Synaptics Scrolling Distance (271):    106, 106
    Synaptics Edge Scrolling (272):    0, 0, 0
    Synaptics Two-Finger Scrolling (273):    1, 1
    Synaptics Move Speed (274):    1.000000, 1.750000, 0.037729, 0.000000
    Synaptics Off (275):    0
    Synaptics Locked Drags (276):    0
    Synaptics Locked Drags Timeout (277):    5000
    Synaptics Tap Action (278):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (279):    1, 3, 0
    Synaptics Circular Scrolling (280):    0
    Synaptics Circular Scrolling Distance (281):    0.100000
    Synaptics Circular Scrolling Trigger (282):    0
    Synaptics Circular Pad (283):    0
    Synaptics Palm Detection (284):    0
    Synaptics Palm Dimensions (285):    10, 200
    Synaptics Coasting Speed (286):    20.000000, 50.000000
    Synaptics Pressure Motion (287):    30, 160
    Synaptics Pressure Motion Factor (288):    1.000000, 1.000000
    Synaptics Resolution Detect (289):    1
    Synaptics Grab Event Device (290):    1
    Synaptics Gestures (291):    1
    Synaptics Capabilities (292):    1, 0, 0, 1, 1, 1, 1
    Synaptics Pad Resolution (293):    46, 42
    Synaptics Area (294):    0, 0, 0, 0
    Synaptics Soft Button Areas (295):    3567, 0, 4071, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (296):    8, 8
    Device Product ID (252):    2, 7
    Device Node (253):    "/dev/input/event5"
```

---

### Post by xc3RnbFO8P on 2014-09-22
Now
> xinput --set-prop 13 "Synaptics Finger" 25 30 256
r&#822;e&#822;s&#822;t&#822;a&#822;r&#822;t&#822; and see if it change anything

my bad dont restart, it will go back 25 30 0

this will make it hard to move the cursor

> xinput --set-prop 13 "Synaptics Finger" 50 80 257

---

### Post by xc3RnbFO8P on 2014-09-22
That looks like your problem:
[http://ken-mcconnell.com/2012/07/22/trackpad-sensitivity-in-ubuntu-on-dell-xps-13/]("http://ken-mcconnell.com/2012/07/22/trackpad-sensitivity-in-ubuntu-on-dell-xps-13/")
> sudo apt-get-install gpointing-device-settings

---

### Post by Tornikee on 2014-09-22
Thanks for the link, will have a look.

---

### Post by pme991 on 2014-09-22
I too am having this same issue.  I have a brand new (< 1 week old) Dell Inspiron 5547.  Cursor randomly jumps to trash icon, along with other issues  (freezing, and auto selecting text).  I am dual booting Windows 8.1 and Ubuntu LTS 14.04.1.  This is very frustrating...

Edit:  Based on this link I think this behavior may be a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1332384]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1332384")  .

---

