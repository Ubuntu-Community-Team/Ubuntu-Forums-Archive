---
title: "Assigning buttons to touchpad corners"
date: 2016-10-24
forum: General Help
---

### Post by epaluoma on 2016-10-24
Hello, I wish to use touchpad corners to navigate, kill a window etc. I tried using synclient (i.e. 'syntclient RTCornerButton=8') to assign right top corner to go back. With mouse this works and I checked with xev that the button is really number 8. And when I'm hitting any of the corners in the touchpad, xev just gives me I'm pressin "1". 


So is there something what I'm missing? Using Lenovo Thinkpad Edge E330.Here's the output of synclient -l

> 
    LeftEdge                = 1548
    RightEdge               = 5394
    TopEdge                 = 1240
    BottomEdge              = 4614
    FingerLow               = 40
    FingerHigh              = 40
    MaxTapTime              = 180
    MaxTapMove              = 261
    MaxDoubleTapTime        = 100
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -118
    HorizScrollDelta        = 118
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0336361
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 8
    RBCornerButton          = 7
    LTCornerButton          = 0
    LBCornerButton          =0
 TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 1
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
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
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 1
    RightButtonAreaLeft     = 3471
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4182
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0





---

