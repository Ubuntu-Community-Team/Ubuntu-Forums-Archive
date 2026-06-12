---
title: "Ubuntu 16.04 Trackpad"
date: 2017-11-08
forum: General Help
---

### Post by corrector on 2017-11-08
Hello,

I have the following Laptop:  Asus Zenbook UX310UAK.

The output from from "xinput --list" gives the following:

```
 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ELAN1200:00 04F3:3044 Touchpad          	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Asus Wireless Radio Control             	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                    	id=11	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
```

So my trackpad is an ELANTECH device.

The following is an output from "xinput --list-props "ELAN1200:00 04F3:3044 Touchpad"

```
Device 'ELAN1200:00 04F3:3044 Touchpad':
	Device Enabled (140):	1
	Coordinate Transformation Matrix (142):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (265):	1
	Device Accel Constant Deceleration (266):	2.500000
	Device Accel Adaptive Deceleration (267):	1.000000
	Device Accel Velocity Scaling (268):	12.500000
	Synaptics Edges (269):	128, 3072, 118, 2080
	Synaptics Finger (270):	9, 12, 0
	Synaptics Tap Time (271):	180
	Synaptics Tap Move (272):	170
	Synaptics Tap Durations (273):	180, 180, 100
	Synaptics ClickPad (274):	1
	Synaptics Middle Button Timeout (275):	0
	Synaptics Two-Finger Pressure (276):	282
	Synaptics Two-Finger Width (277):	7
	Synaptics Scrolling Distance (278):	-77, -77
	Synaptics Edge Scrolling (279):	0, 0, 0
	Synaptics Two-Finger Scrolling (280):	1, 1
	Synaptics Move Speed (281):	1.500000, 3.500000, 0.100000, 0.000000
	Synaptics Off (282):	2
	Synaptics Locked Drags (283):	0
	Synaptics Locked Drags Timeout (284):	5000
	Synaptics Tap Action (285):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (286):	1, 3, 0
	Synaptics Circular Scrolling (287):	0
	Synaptics Circular Scrolling Distance (288):	0.100000
	Synaptics Circular Scrolling Trigger (289):	0
	Synaptics Circular Pad (290):	0
	Synaptics Palm Detection (291):	0
	Synaptics Palm Dimensions (292):	10, 200
	Synaptics Coasting Speed (293):	10.000000, 50.000000
	Synaptics Pressure Motion (294):	30, 160
	Synaptics Pressure Motion Factor (295):	1.000000, 1.000000
	Synaptics Resolution Detect (296):	1
	Synaptics Grab Event Device (297):	0
	Synaptics Gestures (298):	1
	Synaptics Capabilities (299):	1, 0, 0, 1, 1, 0, 0
	Synaptics Pad Resolution (300):	31, 31
	Synaptics Area (301):	0, 0, 0, 0
	Synaptics Soft Button Areas (302):	0, 0, 0, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (303):	19, 19
	Device Product ID (260):	1267, 12356
	Device Node (261):	"/dev/input/event14"
```

Now to the problem 1:

The touchpad works fine if you swipe your finger in a "normal" speed over the surface. But as soon as you need to have some precision, for example getting the pointer to copy a word from the text, the trackpad seems to be "lagging"
So when swiping the finger with slow speed for precision over the surface, it seems like there is a smal delay between the actual movement of my finger, until the actual movement of the pointer on the screen.
Or I suspect that the "resolution" of the trackpad is that bad that my finger actually needs to travel over a set amount of distance to actually trigger the trackpad.

Problem 2:

When ever using Two finger scroll, upon release the trackpad manytimes takes it for a Two finger tap.
Any suggestions on how to tweak this setting?


Does anyone have any similar experience with the above mentioned?

Thanks alot

---

### Post by robertsw on 2018-01-19
Hi-

I think I've got the same problem on my Asus GL503VD.  I'm not sure if I'm seeing the same behaviour on two finger scroll-- can you describe this in more detail?

Other issues I've noticed:
1) A process called something like irq/255-ELAN120 in  top that runs the CPU at 5-10% all the time
2) Sometimes the touchpad stops responding for a time; I think most of the time it comes back after 30-60 seconds.  I believe I can reproduce this freeze by doing a five-finger tap on the touchpad.

Have you seen these?  I'm a bit out of my depth in debugging this issue, so I opened a bug report on kernel.org, where, hopefully, I'll get some help from somebody more knowledgeable.  The bug report is here, in case you're interested:
[https://bugzilla.kernel.org/show_bug.cgi?id=198473](https://bugzilla.kernel.org/show_bug.cgi?id=198473)

Have you had any progress on your touchpad issues in the last months?

---

