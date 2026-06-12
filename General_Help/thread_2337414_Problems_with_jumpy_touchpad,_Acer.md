---
title: "Problems with jumpy touchpad, Acer"
date: 2016-09-17
forum: General Help
---

### Post by trubsee on 2016-09-17
Hi guys I am having troubles with my touchpad it is very slow/jumpy. I can plugin a mouse and it works fine. Here are the settings:
```
Device 'ELAN0501:00 04F3:3019 Touchpad':
    Device Enabled (137):    1
    Coordinate Transformation Matrix (139):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (260):    1
    Device Accel Constant Deceleration (261):    2.500000
    Device Accel Adaptive Deceleration (262):    1.000000
    Device Accel Velocity Scaling (263):    12.500000
    Synaptics Edges (284):    129, 3105, 126, 2211
    Synaptics Finger (285):    25, 30, 0
    Synaptics Tap Time (286):    180
    Synaptics Tap Move (287):    175
    Synaptics Tap Durations (288):    180, 100, 100
    Synaptics ClickPad (289):    1
    Synaptics Middle Button Timeout (290):    0
    Synaptics Two-Finger Pressure (291):    282
    Synaptics Two-Finger Width (292):    7
    Synaptics Scrolling Distance (293):    79, 79
    Synaptics Edge Scrolling (294):    0, 0, 0
    Synaptics Two-Finger Scrolling (295):    1, 1
    Synaptics Move Speed (296):    1.000000, 1.750000, 0.050125, 0.000000
    Synaptics Off (297):    2
    Synaptics Locked Drags (298):    0
    Synaptics Locked Drags Timeout (299):    5000
    Synaptics Tap Action (300):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (301):    1, 3, 0
    Synaptics Circular Scrolling (302):    0
    Synaptics Circular Scrolling Distance (303):    0.100000
    Synaptics Circular Scrolling Trigger (304):    0
    Synaptics Circular Pad (305):    0
    Synaptics Palm Detection (306):    0
    Synaptics Palm Dimensions (307):    10, 200
    Synaptics Coasting Speed (308):    20.000000, 50.000000
    Synaptics Pressure Motion (309):    30, 160
    Synaptics Pressure Motion Factor (310):    1.000000, 1.000000
    Synaptics Resolution Detect (311):    1
    Synaptics Grab Event Device (312):    0
    Synaptics Gestures (313):    1
    Synaptics Capabilities (314):    1, 0, 0, 1, 1, 0, 0
    Synaptics Pad Resolution (315):    32, 32
    Synaptics Area (316):    0, 0, 0, 0
    Synaptics Soft Button Areas (317):    1617, 0, 1916, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (318):    19, 19
    Device Product ID (255):    1267, 12313
    Device Node (256):    "/dev/input/event15"

```

I'm wondering if it is an issue with the driver?

---

### Post by collinjsimpson on 2016-10-13
[COLOR=#111111][FONT=Ubuntu]I experienced a similar issue on my Aspire E-15 (running Ubuntu 16.04). In your BIOS, change the "Touchpad" setting from "Advanced" to "Basic" (if possible). For reference, xinput identifies my touchpad as a "ELAN0501:00 04F3:3019 Touchpad" when the BIOS option is set to "Advanced", and "ETPS/2 Elantech Touchpad" when set to "Basic". I suspect your system may exhibit similar behavior.[/FONT][/COLOR]

---

### Post by martaz2 on 2017-01-18
Thank you very much, [**[COLOR=#000000]collinjsimpson[/COLOR]**]("https://ubuntuforums.org/member.php?u=1737373").
I had the same problem with a new Acer Aspire F 15. Modifying the BIOS seems to have fixed it.
You made my day.

---

### Post by lokithefly on 2017-01-18
I have the same problem but on a Dell. I cannot change me BIOS settings.

---

