---
title: "Help: configure Synaptics touchpad"
date: 2008-07-06
forum: General Help
---

### Post by maury84 on 2008-07-06
Hi you all!
Reading on the web, I've found some articles that descibe how to enable some feature in Synaptics touchpad. How can I do to use these features? I'm really interested about two finger scrolling...
Thanks to anyone wants to help me

Regards,

Maurizio

---

### Post by sayakb on 2008-07-06
At a terminal, type:
```
sudo apt-get install gsynaptics
```Then goto System->Preferences->Touchpad

EDIT: To run GSynaptics, you have to make this setting first. Open a terminal and type:
```
sudo gedit /etc/X11/xorg.conf
``````
Section "InputDevice"
    Identifier    "Synaptics Touchpad"

```Add this line Option "SHMConfig"   "true"  in that file. Mine looks something like this:
```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"            "/dev/psaux"
    Option        "Protocol"          "auto-dev"
    Option        "HorizEdgeScroll"   "0"
  [COLOR=Red]  Option        "SHMConfig"         "true"[/COLOR]
EndSection

```

---

### Post by maury84 on 2008-07-06
Uhm, I've tried, but I can only activate Circular Scrolling (I have no idea of what is it...I've thought something similar of a Synaptics Demo, like the iPod scrollings...unfortunately it seems no works so well...).
Bytheway, here it is the result of synclient -l

Parameter settings:
    LeftEdge                = 102
    RightEdge               = 921
    TopEdge                 = 76
    BottomEdge              = 691
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 220
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 257
    VertScrollDelta         = 15
    HorizScrollDelta        = 20
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.325945
    MaxSpeed                = 0.782269
    AccelFactor             = 0.0065189
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 76
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 0
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 2
    TapButton3              = 3
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 1
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 0
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1

Help please...

---

