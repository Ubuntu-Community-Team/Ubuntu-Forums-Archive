---
title: "(Ubuntu 13.04) Do Away With Right Click on Bottom Right Corner of a Synaptic ClickPad"
date: 2013-06-09
forum: General Help
---

### Post by gristleizer on 2013-06-09
This is probably a dumb question that I'm probably just missing the setting for within synclient, but I hate how, by default, the bottom right corner of my Synaptic ClickPad on my Toshiba Satellite U845T-S4165 doesn't just simply left click for a one-finger click, right click for a two finger click, and middle click for a three finger click. If I happen to be near the bottom right corner when one-finger clicking, it will register as a right click. Though this is how this clickpad was designed to behave (both bottom corners have printed in "buttons" to designate those corners of the clickpad as left and right click buttons), I would prefer that, particularly, the bottom right corner click not register as a right click because it gets in the way when playing some games. Any tips anyone can provide would be greatly appreciated.

---

### Post by ajgreeny on 2013-06-09
You don't say, so have you actually looked at your current synclient settings with **synclient -l**?  That may give you some clues.

---

### Post by gristleizer on 2013-06-09
I have, but RBCornerButton is already set to a value of 0. Is this set in another setting? Here's what comes back when I run synclient -l:
synclient -l
Parameter settings:
    LeftEdge                = 1766
    RightEdge               = 5386
    TopEdge                 = 1640
    BottomEdge              = 4496
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 235
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -107
    HorizScrollDelta        = -107
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0373134
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 428
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 1
    CoastingFriction        = 3
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 1
    RightButtonAreaLeft     = 3576
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4130
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

---

### Post by gristleizer on 2013-06-14
Sorry to bump this, but here is also the output of my xinput list of properties for the touchpad:
beelbo1@beelbuntu:~$ xinput --list-props "SynPS/2 Synaptics TouchPad"
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (133):	1
	Coordinate Transformation Matrix (135):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (256):	1
	Device Accel Constant Deceleration (257):	1.000000
	Device Accel Adaptive Deceleration (258):	1.000000
	Device Accel Velocity Scaling (259):	12.500000
	Synaptics Edges (260):	1766, 5386, 1640, 4496
	Synaptics Finger (261):	25, 30, 256
	Synaptics Tap Time (262):	180
	Synaptics Tap Move (263):	235
	Synaptics Tap Durations (264):	180, 180, 100
	Synaptics ClickPad (265):	1
	Synaptics Tap FastTap (266):	0
	Synaptics Middle Button Timeout (267):	0
	Synaptics Two-Finger Pressure (268):	282
	Synaptics Two-Finger Width (269):	7
	Synaptics Scrolling Distance (270):	-107, -107
	Synaptics Edge Scrolling (271):	0, 0, 0
	Synaptics Two-Finger Scrolling (272):	1, 1
	Synaptics Move Speed (273):	1.000000, 1.750000, 0.037313, 40.000000
	Synaptics Edge Motion Pressure (274):	30, 160
	Synaptics Edge Motion Speed (275):	1, 428
	Synaptics Edge Motion Always (276):	0
	Synaptics Off (277):	0
	Synaptics Locked Drags (278):	0
	Synaptics Locked Drags Timeout (279):	5000
	Synaptics Tap Action (280):	0, 0, 0, 0, 0, 0, 0
	Synaptics Click Action (281):	1, 3, 0
	Synaptics Circular Scrolling (282):	0
	Synaptics Circular Scrolling Distance (283):	0.100000
	Synaptics Circular Scrolling Trigger (284):	0
	Synaptics Circular Pad (285):	0
	Synaptics Palm Detection (286):	0
	Synaptics Palm Dimensions (287):	10, 200
	Synaptics Coasting Speed (288):	1.000000, 3.000000
	Synaptics Pressure Motion (289):	30, 160
	Synaptics Pressure Motion Factor (290):	1.000000, 1.000000
	Synaptics Resolution Detect (291):	1
	Synaptics Grab Event Device (292):	1
	Synaptics Gestures (293):	1
	Synaptics Capabilities (294):	1, 0, 0, 1, 1, 1, 1
	Synaptics Pad Resolution (295):	62, 46
	Synaptics Area (296):	0, 0, 0, 0
	Synaptics Soft Button Areas (297):	3576, 0, 4130, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (298):	8, 8
	Device Product ID (250):	2, 7
	Device Node (251):	"/dev/input/event5"

If anyone could provide me with suggestions as to how to get clicking the bottom right area of the clickpad to simply left click instead of right clicking, that would be great.

---

