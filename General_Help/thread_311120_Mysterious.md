---
title: "Mysterious"
date: 2006-12-02
forum: General Help
---

### Post by bg11 on 2006-12-02
I have linux installed on my laptop.  I use a USB mouse and keyboard since my laptop mouse buttons are broken.  The problem I have is that sometimes, at random, my pointer sinks to the bottom of the screen all by itself, after which the keyboards (both on board the laptop and USB one) get disabled.  Any attempt to move the pointer using the mouse results in the same behaviour: the pointer automatically moves to the very bottom of the screen.  It's so quick that I'm unable to save and close applications, my only recourse is to manually restart my laptop, which has led to me losing data! :cry:

I decided to disable my touch pad hoping that it would help, so I installed synaptics and disabled it.  But this didn't prevent the problem.

This problem happens at random every couple of days, google has been very unhelpful on this matter, any suggestions or ideas at all, anything?

       cheers

---

### Post by bg11 on 2006-12-03
I thought I'd post part of my xorg.conf file too, in case it helps:

```

Section "ServerLayout"
        Identifier     "XFree86 Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "PS/2 Mouse" "CorePointer"
# Serial Mouse not detected
        InputDevice    "USB Mouse" "CorePointer"
        InputDevice    "ALPS TouchPad" "AlwaysCore"
# Synaptics TouchPad not detected
EndSection

Section "ServerFlags"
        Option "AllowMouseOpenFail"  "true"

EndSection

Section "InputDevice"
        Identifier  "Serial Mouse"
        Driver      "mouse"
        Option      "Protocol" "Microsoft"
        Option      "Device" "/dev/ttyS0"
        Option      "Emulate3Buttons" "true"
        Option      "Emulate3Timeout" "70"
        Option      "SendCoreEvents"  "true"
EndSection

Section "InputDevice"
        Identifier  "PS/2 Mouse"
        Driver      "mouse"
        Option      "Protocol" "IMPS/2"
Option          "ZAxisMapping"          "4 5"
        Option      "Device" "/dev/psaux"
        Option      "Emulate3Buttons" "true"
        Option      "Emulate3Timeout" "70"
        Option      "SendCoreEvents"  "true"
EndSection

Section "InputDevice"
        Identifier      "USB Mouse"
        Driver          "mouse"
        Option          "Device"                "/dev/input/mice"
        Option          "SendCoreEvents"        "true"
        Option          "Protocol"              "IMPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "5"
EndSection

Section "InputDevice"
        Identifier      "ALPS TouchPad"
        Driver          "synaptics"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "on"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "20"
        Option          "MinSpeed"              "0.2"
        Option          "MaxSpeed"              "0.5"
        Option          "AccelFactor"           "0.01"
        Option          "EdgeMotionMinSpeed"    "15"
        Option          "EdgeMotionMaxSpeed"    "15"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
EndSection

Section "InputDevice"
        Identifier      "Synaptics TouchPad"
        Driver          "synaptics"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "LeftEdge"              "1700"
        Option          "RightEdge"             "5300"
        Option          "TopEdge"               "1700"
        Option          "BottomEdge"            "4200"
        Option          "FingerLow"             "25"
        Option          "FingerHigh"            "30"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
        Option          "VertScrollDelta"       "100"
        Option          "MinSpeed"              "0.06"
        Option          "MaxSpeed"              "0.12"
        Option          "AccelFactor"           "0.0010"
        Option          "SHMConfig"             "on"
        Option          "Repeater"              "/dev/ps2mouse"
EndSection

```

---

