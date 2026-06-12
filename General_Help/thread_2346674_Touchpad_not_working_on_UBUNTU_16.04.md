---
title: "Touchpad not working on UBUNTU 16.04"
date: 2016-12-17
forum: General Help
---

### Post by strubloid on 2016-12-17
I tried a lot of things i will post all the forums that i passed:

My computer is a toshiba L-50c-22Q

[https://ubuntuforums.org/showthread.php?t=2322413](https://ubuntuforums.org/showthread.php?t=2322413) (for me isn't solved)

```
1 - Installed the new input-synnaptics:
apt-cache policy xserver-xorg-input-synaptics
xserver-xorg-input-synaptics:
  Installed: 1.8.2-1ubuntu3
  Candidate: 1.8.2-1ubuntu3

2 - Tried to turn on by terminal:
[COLOR=#111111][FONT=Ubuntu]Turn touchpad ON: synclient TouchpadOff=0 Turn touchpad OFF: synclient TouchpadOff=1[/FONT][/COLOR]

3 - synclient -lParameter settings:
    LeftEdge                = 130
    RightEdge               = 3130
    TopEdge                 = 105
    BottomEdge              = 1851
    FingerLow               = 1
    FingerHigh              = 1
    MaxTapTime              = 180
    MaxTapMove              = 167
    MaxDoubleTapTime        = 100
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 76
    HorizScrollDelta        = 76
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 1
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 2
    AccelFactor             = 0.075
    TouchpadOff             = 2
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 8
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 1
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 7
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 8
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 19
    VertHysteresis          = 19
    ClickPad                = 1
    RightButtonAreaLeft     = 1630
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1603
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0
```

If you can help me i will be very happy to reply you, thanks for this craic! slainte!

Just adding some more information:

```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v7.0	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v7.0	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v7.0	id=10	[slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                 	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; Toshiba input device                    	id=16	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v7.0	id=17	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v7.0	id=18	[slave  keyboard (3)]
```

---

### Post by mörgæs on 2016-12-18
In the thread to which you linked I suggested a live boot of 16.10. How did that work?

---

