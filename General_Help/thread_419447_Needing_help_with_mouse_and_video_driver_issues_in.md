---
title: "Needing help with mouse and video driver issues in Feisty"
date: 2007-04-23
forum: General Help
---

### Post by catalytic on 2007-04-23
Please please please, someone help me figure these issues out...

1. Mouse decided when it want to accept clicks, keyboard works fine. But the mouse is driving me insane. I have tried several things, all I can come up with is that the latest kernel has been known to cause this issue. 

2. After installing Feisty for the 3rd time in as many days (mainly due to me trying to configure my at card) Feisty only recognises my card as generic. I have an ATI 9250 Pro (at first feisty did recognise this as a 9200 pro). My problems occured trying to install the control panel, so I could plug in my other monitor.

This is what my xorg.conf files looks like:

 41:Section "InputDevice"
42-     Identifier      "Generic Keyboard"
43-     Driver          "kbd"
44-     Option          "CoreKeyboard"
45-     Option          "XkbRules"      "xorg"
46-     Option          "XkbModel"      "pc105"
47-     Option          "XkbLayout"     "us"
48-EndSection
49-
50:Section "InputDevice"
51-     Identifier      "Configured Mouse"
52-     Driver          "mouse"
53-     Option          "CorePointer"
54-     Option          "Device"                "/dev/input/mice"
55-     Option          "Protocol"              "ImPS/2"
56-     Option          "ZAxisMapping"          "4 5"
57-     Option          "Emulate3Buttons"       "true"
58-EndSection
59-
60:Section "InputDevice"
61-     Driver          "wacom"
62-     Identifier      "stylus"
63-     Option          "Device"        "/dev/input/wacom"
64-     Option          "Type"          "stylus"
65-     Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
66-EndSection
67-
68:Section "InputDevice"
69-     Driver          "wacom"
70-     Identifier      "eraser"
71-     Option          "Device"        "/dev/input/wacom"
72-     Option          "Type"          "eraser"
73-     Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
74-EndSection
75-
76:Section "InputDevice"
77-     Driver          "wacom"
78-     Identifier      "cursor"
79-     Option          "Device"        "/dev/input/wacom"
80-     Option          "Type"          "cursor"
81-     Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
82-EndSection
83-
84-Section "Device"
85-     Identifier      "Generic Video Card"
86-     Driver          "ati"
--
131:    InputDevice     "Generic Keyboard"
132:    InputDevice     "Configured Mouse"
133:    InputDevice     "stylus"        "SendCoreEvents"
134:    InputDevice     "cursor"        "SendCoreEvents"
135:    InputDevice     "eraser"        "SendCoreEvents"
136-EndSection
137-
138-Section "DRI"
139-    Mode    0666
140-EndSection

---

