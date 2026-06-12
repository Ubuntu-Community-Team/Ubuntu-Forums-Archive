---
title: "make laptop touchpad &quot;old school&quot; - no multitouch"
date: 2014-03-22
forum: General Help
---

### Post by lndbrusr on 2014-03-22
Hello,

I just changed my dad over from winxp to lubuntu 13.10 on a dell latitude d620.  Lubuntu works well on this old piece of hw.

My dad has problems with his fingers where he has limited sense of feeling in them.  He is used to the non multitouch touchpad from when windows xp was on this hw and the multitouch with lubuntu is causing him problems.

I think that I need to change certain values in xinput.  I don't know which values to change to make the touchpad "old school".  Can someone help me out with this or tell me another way to accomplish this?

Thanks,
cj

dad@dad-laptop:~$ xinput list-props 11
Device 'AlpsPS/2 ALPS DualPoint TouchPad':
    Device Enabled (146):    1
    Coordinate Transformation Matrix (148):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (268):    1
    Device Accel Constant Deceleration (269):    2.500000
    Device Accel Adaptive Deceleration (270):    1.000000
    Device Accel Velocity Scaling (271):    12.500000
    Synaptics Edges (291):    153, 870, 115, 652
    Synaptics Finger (292):    12, 15, 0
    Synaptics Tap Time (293):    180
    Synaptics Tap Move (294):    56
    Synaptics Tap Durations (295):    180, 180, 100
    Synaptics ClickPad (296):    0
    Synaptics Middle Button Timeout (297):    75
    Synaptics Two-Finger Pressure (298):    141
    Synaptics Two-Finger Width (299):    7
    Synaptics Scrolling Distance (300):    25, 25
    Synaptics Edge Scrolling (301):    1, 0, 0
    Synaptics Two-Finger Scrolling (302):    0, 0
    Synaptics Move Speed (303):    1.000000, 1.750000, 0.156495, 0.000000
    Synaptics Off (304):    0
    Synaptics Locked Drags (305):    0
    Synaptics Locked Drags Timeout (306):    5000
    Synaptics Tap Action (307):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (308):    1, 1, 0
    Synaptics Circular Scrolling (309):    0
    Synaptics Circular Scrolling Distance (310):    0.100000
    Synaptics Circular Scrolling Trigger (311):    0
    Synaptics Palm Detection (312):    0
    Synaptics Palm Dimensions (313):    10, 100
    Synaptics Coasting Speed (314):    20.000000, 50.000000
    Synaptics Pressure Motion (315):    15, 80
    Synaptics Pressure Motion Factor (316):    1.000000, 1.000000
    Synaptics Resolution Detect (317):    1
    Synaptics Grab Event Device (318):    1
    Synaptics Gestures (319):    1
    Synaptics Capabilities (320):    1, 1, 1, 0, 0, 1, 0
    Synaptics Pad Resolution (321):    1, 1
    Synaptics Area (322):    0, 0, 0, 0
    Synaptics Noise Cancellation (323):    6, 6
    Device Product ID (263):    2, 8
    Device Node (264):    "/dev/input/event10"
dad@dad-laptop:~$

---

### Post by Rex Bouwense on 2014-03-22
If he has problem with feeling in his fingers, perhaps you should buy him a wireless mouse.  Most work out of the box.

---

### Post by lndbrusr on 2014-03-23
We tried the mouse and a combo of:

-he has trouble controlling the mouse and knowing if he is hitting the left and right buttons
-he is adverse to change (imagine how this is going moving him from XP to lubuntu) and it would be best if I can get the touchpad to do nothing but act as a mouse pointer like it was before.

---

### Post by Rex Bouwense on 2014-03-23
Understand.  I am sure he will thoroughly enjoy Lubuntu after he uses it for a while.  I think this is what you are after:
[https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings](https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings)

---

### Post by lndbrusr on 2014-03-24
Thanks... 

This ended up working:

 Option "TouchpadOff" "integer"
              Switch off the touchpad.  Valid values are:

              0   Touchpad is enabled
              1   Touchpad is switched off
              2   Only tapping and scrolling is switched off
              Property: "Synaptics Off"

dad@dad-laptop:~$ synclient -l | grep Touchpad
    TouchpadOff             = 0
dad@dad-laptop:~$ synclient TouchpadOff=2
dad@dad-laptop:~$  

I also added this synclient command to my autostart file so it is persistent through reboot and login.

Thanks,
cj

---

### Post by Rex Bouwense on 2014-03-24
Great.  Here's hoping that he enjoys Lubuntu as much as the rest of us using it do.

---

