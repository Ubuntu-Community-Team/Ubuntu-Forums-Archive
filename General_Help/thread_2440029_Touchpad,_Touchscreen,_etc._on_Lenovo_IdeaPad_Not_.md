---
title: "Touchpad, Touchscreen, etc. on Lenovo IdeaPad Not Working After Update"
date: 2020-04-04
forum: General Help
---

### Post by ciamele on 2020-04-04
Hello,

I could use some help. I tried Googling the issues, but alas, I'm not having any luck.

**_Issues:_**
[LIST]
[*]Touchpad, touchscreen, USB to NIC dongle are no longer working
[*](onboard) Backport wifi adapter no longer working
[/LIST]


**_Chain of Events (over the course of a month+):_**
[LIST]
[*]Everything was working fine...
[*]Installed the update 5.3.0-40-generic (and related packages) when the update manager alerted me to available updates
[*]My backport wifi driver failed to work
[*]This has happened numerous times in the past, so I followed the instructions [here]("https://ubuntuforums.org/showthread.php?t=2400595") to attempt to resolve as usual
[*]Upon booting to 5.3.0-40, I could decrypt the drive, however the system would freeze at the login screen
[*]I was unable to resolve the freeze, but could still boot to 5.3.0-28 by choosing it from the GRUB2 menu
[*]I decided to wait out the issue and hope a further kernel update would solve my freezing issue
[*]Continuing to use the system from 5.3.0-28, Ubuntu notified me of updates (not kernel). I installed them
[*]After rebooting, GRUB2 booted to it's own recovery prompt
[*]There weren't options for any of my operating systems (dual boot with Windows)
[*]I repaired GRUB2 from instructions [here]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting")
[*]Booted back into 5.3.0-28 and manually updated to kernel 5.3.0-42
[*]After reboot in 5.3.0-42, freezing issue was resolved
[*]Old issue of backport wifi driver failing to work remained
[*]New issue of touchpad not working at all
[*]New issue of USB to NIC dongle does not work
[*]New issue of touchscreen functionality does not work
[*]Boot back into 5.3.0-28 and manually updated to kernel 5.3.0-45
[*]wifi driver, touchpad, and USB to NIC dongle, and touchscreen continue to be an issue after reboot into 5.3.0-45
[/LIST]


**_Additional Info:_**
[LIST]
[*]My Ubuntu 18.04 installation is encrypted
[*]I am able to use a USB mouse in 5.3.0-45
[*]The USB to NIC dongle is visible with lsusb
[*]USB to NIC dongle not listed under ifconfig
[*]USB to NIC Model Plugable USB2-E100
[*]Unplugging and re-plugging in the dongle has no effect
[*]wifi adapter does not show under ifconfig
[*]The touchpad does not show in xinput list
[*]Touchscreen not visible in xinput list
[*]Laptop model is IdeaPad Flex 14 IML Model Name 81XG
[/LIST]


lsusb (from 5.3.0-28)
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 06cb:00be Synaptics, Inc.
Bus 001 Device 002: ID 5986:2115 Acer, Inc
Bus 001 Device 004: ID 8087:0aaa Intel Corp.
Bus 001 Device 005: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

xinput list (from 5.3.0-28)
```
&#9121; Virtual core pointer                         id=2     [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                   id=4     [slave  pointer  (2)]
&#9116;   &#8627; MSFT0001:02 06CB:7F28 Touchpad               id=10     [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 51C4 Pen stylus                    id=11     [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 51C4 Finger touch                  id=12     [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 51C4 Pen eraser                    id=15     [slave  pointer  (2)]
&#9123; Virtual core keyboard                        id=3     [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                  id=5     [slave  keyboard (3)]
    &#8627; Power Button                                 id=6     [slave  keyboard (3)]
    &#8627; Video Bus                                    id=7     [slave  keyboard (3)]
    &#8627; Power Button                                 id=8     [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C              id=9     [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                        id=13     [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                 id=14     [slave  keyboard (3)]
```

 xinput list-props 10 (from 5.3.0-28)
```
Device 'MSFT0001:02 06CB:7F28 Touchpad':
     Device Enabled (168):     1
     Coordinate Transformation Matrix (170):     1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
     Device Accel Profile (296):     1
     Device Accel Constant Deceleration (297):     2.500000
     Device Accel Adaptive Deceleration (298):     1.000000
     Device Accel Velocity Scaling (299):     12.500000
     Synaptics Edges (300):     48, 1176, 43, 761
     Synaptics Finger (301):     25, 30, 0
     Synaptics Tap Time (302):     180
     Synaptics Tap Move (303):     64
     Synaptics Tap Durations (304):     180, 180, 100
     Synaptics ClickPad (305):     1
     Synaptics Middle Button Timeout (306):     0
     Synaptics Two-Finger Pressure (307):     282
     Synaptics Two-Finger Width (308):     7
     Synaptics Scrolling Distance (309):     -29, 29
     Synaptics Edge Scrolling (310):     0, 0, 0
     Synaptics Two-Finger Scrolling (311):     1, 1
     Synaptics Move Speed (312):     1.000000, 1.750000, 0.136612, 0.000000
     Synaptics Off (313):     0
     Synaptics Locked Drags (314):     0
     Synaptics Locked Drags Timeout (315):     5000
     Synaptics Tap Action (316):     2, 3, 0, 0, 1, 0, 0
     Synaptics Click Action (317):     1, 0, 0
     Synaptics Circular Scrolling (318):     0
     Synaptics Circular Scrolling Distance (319):     0.100000
     Synaptics Circular Scrolling Trigger (320):     0
     Synaptics Circular Pad (321):     0
     Synaptics Palm Detection (322):     1
     Synaptics Palm Dimensions (323):     10, 200
     Synaptics Coasting Speed (324):     20.000000, 50.000000
     Synaptics Pressure Motion (325):     30, 160
     Synaptics Pressure Motion Factor (326):     1.000000, 1.000000
     Synaptics Resolution Detect (327):     1
     Synaptics Grab Event Device (328):     0
     Synaptics Gestures (329):     1
     Synaptics Capabilities (330):     1, 0, 0, 1, 1, 0, 0
     Synaptics Pad Resolution (331):     12, 12
     Synaptics Area (332):     0, 0, 0, 0
     Synaptics Soft Button Areas (333):     612, 0, 659, 0, 0, 0, 0, 0
     Synaptics Noise Cancellation (334):     7, 7
     Device Product ID (292):     1739, 32552
     Device Node (291):     "/dev/input/event14"
```

lsusb output (from 5.3.0-45)
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 06cb:00be Synaptics, Inc.
Bus 001 Device 002: ID 5986:2115 Acer, Inc
Bus 001 Device 006: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 004: ID 8087:0aaa Intel Corp.
Bus 001 Device 005: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

xinput list (from 5.3.0-45)
```
&#9121; Virtual core pointer                         id=2     [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                   id=4     [slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse                   id=9     [slave  pointer  (2)]
&#9123; Virtual core keyboard                        id=3     [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                  id=5     [slave  keyboard (3)]
    &#8627; Power Button                                 id=6     [slave  keyboard (3)]
    &#8627; Power Button                                 id=7     [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                 id=8     [slave  keyboard (3)]
```


**_Thoughts:_**
[LIST]
[*]I suspect the touchpad, touchscreen, and USB to NIC issues are all related
[*]Clearly a number of other items are not loading properly when comparing the xinput lists between kernels
[*]I've scanned though Utilities > Logs, but have not noticed anything that stands out
[/LIST]


**_Questions:_**
[LIST=1]
[*]Would repairing Ubuntu packages solve the issue, and if so, can it be done with a live USB (given the network access issue)?
[*]Is there a specific log I should be looking at that would tell me what happened? If so, can you walk me through finding it?
[/LIST]


Any thoughts or assistance would be greatly appreciated. Thanks!

---

### Post by ciamele on 2020-04-19
I know everyone is on pins and needles to see what happened considering the only views of this thread were mine...

Should anyone in a similar situation find this post in the hope it will solve their problem, I'll share my non-solution. After two weeks of off-and-on troubleshooting, testing, Googling, and sacrificing chickens to the computer gods, I did the following:
[LIST=1]
[*]removed all of the new kernels that didn't work using the instructions [here]("https://askubuntu.com/questions/343066/how-to-delete-a-non-working-kernel-after-update").
[*]updated GRUB (because the above instructions did not change the menu) with the instructions [here]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting").
[/LIST]

I couldn't possibly list all the things I tried along the way, but I do know reinstalling the kernels didn't help. So I have not yet attempted to reinstall them after the purge. I've had my fill of this fun for a while despite not having the more updated (secure) kernels.

Like I said, it's a non-solution. But maybe this will save someone else the uncounted hours I spent.

---

