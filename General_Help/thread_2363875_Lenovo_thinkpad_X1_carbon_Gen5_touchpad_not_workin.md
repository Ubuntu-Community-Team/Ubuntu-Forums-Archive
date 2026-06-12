---
title: "Lenovo thinkpad X1 carbon Gen5 touchpad not working"
date: 2017-06-15
forum: General Help
---

### Post by sebastiaan5 on 2017-06-15
Today my new Lenovo thinkpad X1 carbon arrived. I did some research before and this supposed to be a very well support Linux laptop as not the best according to some sites. But my touchpad is not working :/

journalctl output:

```

Jun 15 22:22:33 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unhandled HKEY event 0x60b0
Jun 15 22:22:33 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
Jun 15 22:22:34 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unknown possible thermal alarm or keyboard event received
Jun 15 22:22:34 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unhandled HKEY event 0x60b1
Jun 15 22:22:34 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
Jun 15 22:23:18 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unknown possible thermal alarm or keyboard event received
Jun 15 22:23:18 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unhandled HKEY event 0x60b0
Jun 15 22:23:18 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
Jun 15 22:23:19 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unknown possible thermal alarm or keyboard event received
Jun 15 22:23:19 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unhandled HKEY event 0x60b1
Jun 15 22:23:19 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
Jun 15 22:23:24 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:24 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:24 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:24 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:24 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:24 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: issuing reconnect request
Jun 15 22:23:25 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: synaptics: queried max coordinates: x [..5678], y [..4758]
Jun 15 22:23:25 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: synaptics: queried min coordinates: x [1266..], y [1094..]
Jun 15 22:23:29 sevaho-ThinkPad-X1-Carbon-5th dbus[726]: [system] Activating service name='com.ubuntu.SoftwareProperties' (using servicehelper)
Jun 15 22:23:29 sevaho-ThinkPad-X1-Carbon-5th dbus[726]: [system] Successfully activated service 'com.ubuntu.SoftwareProperties'
Jun 15 22:23:48 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:48 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:48 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:48 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:48 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 15 22:23:48 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: issuing reconnect request
Jun 15 22:23:49 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: synaptics: queried max coordinates: x [..5678], y [..4758]
Jun 15 22:23:49 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio1: synaptics: queried min coordinates: x [1266..], y [1094..]
Jun 15 22:23:50 sevaho-ThinkPad-X1-Carbon-5th kernel: psmouse serio2: Failed to reset mouse on synaptics-pt/serio0

```

xinput list-props 11 output:

```

Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (140):    1
    Coordinate Transformation Matrix (142):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (264):    1
    Device Accel Constant Deceleration (265):    2.500000
    Device Accel Adaptive Deceleration (266):    1.000000
    Device Accel Velocity Scaling (267):    12.500000
    Synaptics Edges (268):    1574, 5370, 1350, 4502
    Synaptics Finger (269):    25, 30, 0
    Synaptics Tap Time (270):    180
    Synaptics Tap Move (271):    252
    Synaptics Tap Durations (272):    180, 100, 100
    Synaptics ClickPad (273):    1
    Synaptics Middle Button Timeout (274):    0
    Synaptics Two-Finger Pressure (275):    282
    Synaptics Two-Finger Width (276):    7
    Synaptics Scrolling Distance (277):    114, 114
    Synaptics Edge Scrolling (278):    0, 0, 0
    Synaptics Two-Finger Scrolling (279):    1, 1
    Synaptics Move Speed (280):    1.000000, 1.750000, 0.034874, 0.000000
    Synaptics Off (281):    2
    Synaptics Locked Drags (282):    0
    Synaptics Locked Drags Timeout (283):    5000
    Synaptics Tap Action (284):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (285):    1, 3, 0
    Synaptics Circular Scrolling (286):    0
    Synaptics Circular Scrolling Distance (287):    0.100000
    Synaptics Circular Scrolling Trigger (288):    0
    Synaptics Circular Pad (289):    0
    Synaptics Palm Detection (290):    0
    Synaptics Palm Dimensions (291):    10, 200
    Synaptics Coasting Speed (292):    20.000000, 50.000000
    Synaptics Pressure Motion (293):    30, 160
    Synaptics Pressure Motion Factor (294):    1.000000, 1.000000
    Synaptics Resolution Detect (295):    1
    Synaptics Grab Event Device (296):    0
    Synaptics Gestures (297):    1
    Synaptics Capabilities (298):    1, 0, 0, 1, 1, 1, 1
    Synaptics Pad Resolution (299):    1, 1
    Synaptics Area (300):    0, 0, 0, 0
    Synaptics Soft Button Areas (301):    3472, 0, 4098, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (302):    28, 28
    Device Product ID (258):    2, 7
    Device Node (259):    "/dev/input/event5"


```

I can't figure out what I am missing, any clues?

---

### Post by gordintoronto on 2017-06-15
What version of Linux are you using? With the very latest hardware, you should use the very latest OS. I would try the development version, 17.10.

---

### Post by sebastiaan5 on 2017-06-16
So I have a fix for it, but it's a hack, I have disabled trackpoint in the bios. Now it works except the trackpont . My BIOS is also version 1.16 and current is 1.18 I'll try to flash it. 

still journal keeps telling me errors:

```

hinkPad-X1-Carbon-5th:~$ journalctl -f
-- Logs begin at Fre 2017-06-16 08:27:10 CEST. --
Jun 16 08:33:59 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
Jun 16 08:34:06 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unknown possible thermal alarm or keyboard event received
Jun 16 08:34:06 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unhandled HKEY event 0x60b0
Jun 16 08:34:06 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
Jun 16 08:34:15 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unknown possible thermal alarm or keyboard event received
Jun 16 08:34:15 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unhandled HKEY event 0x60b1
Jun 16 08:34:15 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
Jun 16 08:34:37 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unknown possible thermal alarm or keyboard event received
Jun 16 08:34:37 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unhandled HKEY event 0x60b0
Jun 16 08:34:37 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
Jun 16 08:35:03 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unknown possible thermal alarm or keyboard event received
Jun 16 08:35:03 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: unhandled HKEY event 0x60b1
Jun 16 08:35:03 sevaho-ThinkPad-X1-Carbon-5th kernel: thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net



```

---

