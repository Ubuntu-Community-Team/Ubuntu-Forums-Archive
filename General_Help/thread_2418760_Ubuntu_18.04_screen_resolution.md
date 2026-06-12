---
title: "Ubuntu 18.04 screen resolution"
date: 2019-05-10
forum: General Help
---

### Post by microlifecc on 2019-05-10
I just upgraded from 16.04 to 18.04. Now my monitor is stuck at a resolution of :
> 
    xrandr
    xrandr: Failed to get size of gamma for output default Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480 default connected primary 640x480+0+0 0mm x 0mm    640x480       73.00*

> xrandr --verbose
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 (0x2aa) normal (normal) 0mm x 0mm
    Identifier: 0x2a9
    Timestamp:  66608
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    _MUTTER_PRESENTATION_OUTPUT: 0 
  640x480 (0x2aa) 22.426MHz *current
        h: width   640 start    0 end    0 total  640 skew    0 clock  35.04KHz
        v: height  480 start    0 end    0 total  480           clock  73.00Hz

> xrandr -s 6
Size index 6 is too large, there are only 1 sizes

Also my grub doesn't have nomodeset mentioned.

Any help please?

---

### Post by Autodave on 2019-05-11
Can we have some info like the model of your computer, any changes made to it like a graphics card?  Monitor specs or model?

Unfortunately, from my own experience, upgrades usually don't work.  Others never have a problem.  I have learned the hard way to just do clean installs to prevent problems like you are having.

---

