---
title: "Best way to &quot;tune&quot; Synaptics settings?"
date: 2013-04-28
forum: General Help
---

### Post by csete on 2013-04-28
I have a Sony Vaio 15T laptop with Ubuntu 13.04 installed via upgrade from 12.10.  While I've never been thrilled with the touchpad behavior on this machine, it seems to be worse since the upgrade to 13.04 and I'm struggling to get it "tuned" to with settings that don't drive me crazy.  dmesg tells me:

```

[    0.232787] pnp 00:08: Plug and Play ACPI device, IDs SNYa00b SYN0300 SYN0002 PNP0f13 (active)
[   19.583664] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x127c00, board id: 1999, fw id: 1106483
[   19.618090] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8

```

The things that I want in terms of functionality include:
[LIST]
[*]Two-finger scroll
[*]Natural scroll
[*]Tap to click
[*]
[/LIST]

I've disabled Gnome controlling the touchpoint to allow my XOrg settings to stick, since "natural scrolling" and Gnome "smooth scrolling" don't get along.  Unfortunately, as it stands, despite reading and re-reading the synaptics driver docs and various web sites I can't seem to get things tuned up.  Right now, I have to tap very hard to get it to register the click.  Many times, the cursor moves as I'm attempting to click and "local" accuracy is not great.  Finally, despite having palm detect enabled, I seem to still have the cursor jump at times while typing.  

My XOrg settings are:

```

Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "VertScrollDelta" "-107"
        Option "HorizScrollDelta" "-107"
        Option "PalmDetect" "1"
        Option "SHMConfig" "on"
EndSection

```

The complete list of settings are:

```

Parameter settings:
    LeftEdge                = 1766
    RightEdge               = 5388
    TopEdge                 = 1643
    BottomEdge              = 4535
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 237
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -107
    HorizScrollDelta        = -107
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0371264
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 430
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
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
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 1
    RightButtonAreaLeft     = 3577
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4164
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```

I could really use suggestions or points to any tools to try to better tune this behavior.  As it stands, it is really starting to drive me a bit crazy.

Thanks so much,
Craig

---

