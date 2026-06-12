---
title: "SynPS/2 Snaptics Touchpad not working"
date: 2015-07-30
forum: General Help
---

### Post by bublz2 on 2015-07-30
Hello there :)

I have a problem with my touchpad, I am not able to move the mouse with the touchpad but I am able to right click or left click items. I can only move the cursor with my mouse. Can anyone help me fix this problem please ? I tried looking around but haven't found anyone that has had this issue before... (P.S i have the Touchpad enabled)

---

### Post by abram2 on 2015-11-07
I'm having the same issue after an update running Xubuntu 14.04.1 under kernel version 3.19.0-32-generic. Not sure what's going on yet. I did some googling and tried to update /etc/default/grub with some suggested workarounds, but it doesn't see to be the same issue. I'm suspecting a configuration file got updated, but no clues as of yet. Here is some output from xinput and tpconfig for the record. 


$ xinput list-props "SynPS/2 Synaptics TouchPad"
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (138):    1
    Coordinate Transformation Matrix (140):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (265):    2
    Device Accel Constant Deceleration (266):    1.000000
    Device Accel Adaptive Deceleration (267):    1.000000
    Device Accel Velocity Scaling (268):    10.000000
    Device Product ID (255):    2, 7
    Device Node (256):    "/dev/input/event4"
    Evdev Axis Inversion (269):    0, 0
    Evdev Axis Calibration (270):    <no items>
    Evdev Axes Swap (271):    0
    Axis Labels (272):    "Abs MT Position X" (263), "Abs MT Position Y" (264), "Abs Pressure" (261), "Abs Tool Width" (262), "None" (0), "None" (0)
    Button Labels (273):    "Button Left" (141), "Button Unknown" (258), "Button Right" (143), "Button Wheel Up" (144), "Button Wheel Down" (145)
    Evdev Middle Button Emulation (274):    0
    Evdev Middle Button Timeout (275):    50
    Evdev Third Button Emulation (276):    0
    Evdev Third Button Emulation Timeout (277):    1000
    Evdev Third Button Emulation Button (278):    3
    Evdev Third Button Emulation Threshold (279):    20
    Evdev Wheel Emulation (280):    0
    Evdev Wheel Emulation Axes (281):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (282):    10
    Evdev Wheel Emulation Timeout (283):    200
    Evdev Wheel Emulation Button (284):    4
    Evdev Drag Lock Buttons (285):    0

$ tpconfig -i
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;		no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.


Any insight is much appreciated!

---

### Post by abram2 on 2015-11-07
Making head way. I installed xserver-xorg-input-synaptics as per the instructions on [https://askubuntu.com/questions/595136/toshiba-satellite-p745-touchpad-problem/596116#596116](https://askubuntu.com/questions/595136/toshiba-satellite-p745-touchpad-problem/596116#596116). I know the touchpad is working, but now i have no cursor. Hah! Back to the googling board to see what's causing that.

---

### Post by abram2 on 2015-11-07
Got it! Something got borked in my ~/.config/xfce directory. I created a new user on the system and moved that folder into my home folder to reset the xfce settings back to default. Just thought I would post the follow-ups in the event someone has the same issues.

---

