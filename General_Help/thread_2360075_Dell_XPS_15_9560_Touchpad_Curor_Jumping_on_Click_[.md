---
title: "Dell XPS 15 9560 Touchpad Curor Jumping on Click [16.04]"
date: 2017-05-01
forum: General Help
---

### Post by samlighty94 on 2017-05-01
Hi,

I've installed Ubuntu alongside Win 10 on my XPS 15 9560.  There is an issue with the touchpad where the cursor jumps across the screen when clicking.

The libinput driver is in use, which I believe is the default 16.04 driver for the touchpad.  Below is some relevant info:

$ xinput list
```
SynPS/2 Synaptics TouchPad                  id=18    [slave  pointer  (2)]

```
$ xinput list-props 18
```

Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (140):    1
    Coordinate Transformation Matrix (142):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Tapping Enabled (293):    1
    libinput Tapping Enabled Default (294):    0
    libinput Tapping Drag Enabled (295):    1
    libinput Tapping Drag Enabled Default (296):    1
    libinput Tapping Drag Lock Enabled (297):    0
    libinput Tapping Drag Lock Enabled Default (298):    0
    libinput Accel Speed (276):    0.000000
    libinput Accel Speed Default (277):    0.000000
    libinput Natural Scrolling Enabled (281):    0
    libinput Natural Scrolling Enabled Default (282):    0
    libinput Send Events Modes Available (260):    1, 1
    libinput Send Events Mode Enabled (261):    0, 0
    libinput Send Events Mode Enabled Default (262):    0, 0
    libinput Left Handed Enabled (283):    0
    libinput Left Handed Enabled Default (284):    0
    libinput Scroll Methods Available (285):    1, 1, 0
    libinput Scroll Method Enabled (286):    1, 0, 0
    libinput Scroll Method Enabled Default (287):    1, 0, 0
    libinput Click Methods Available (299):    1, 1
    libinput Click Method Enabled (300):    1, 0
    libinput Click Method Enabled Default (301):    1, 0
    libinput Disable While Typing Enabled (302):    1
    libinput Disable While Typing Enabled Default (303):    1
    Device Node (263):    "/dev/input/event9"
    Device Product ID (264):    2, 7
    libinput Drag Lock Buttons (292):    <no items>
    libinput Horizonal Scroll Enabled (265):    1

```

After extensive searching I cannot find a solution that has worked for this issue.

Thanks

---

### Post by ihendley on 2017-05-27
I have the same problem. It happens specifically when using two fingers - one to move the pointer around and one to click. If I click before lifting the other finger then the cursor jumps. It's very hard to only use one finger at a time, so this basically renders the touchpad unusable. All solutions suggested elsewhere such as changing the driver from synaptics to libinput have failed so far. 

[This]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1574667") bug report is likely the same issue.

---

