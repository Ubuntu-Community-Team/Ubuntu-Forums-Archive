---
title: "Third Button Emulation doesn't work with touchscreen"
date: 2012-11-30
forum: General Help
---

### Post by Aptorian on 2012-11-30
Has anybody with a touchscreen actually been able to make the evdev driver's third button emulation (ie: hold for right click) work? 

I added the appropriate lines to /usr/share/X11/xorg.conf.d/10-evdev.conf and logged out and back in...

```
Option "EmulateThirdButton" "1"
Option "EmulateThirdButtonButton" "3"
Option "EmulateThirdButtonTimeout" "750"
Option "EmulateThirdButtonThreshold" "50"
```

...and the properties are indeed set when I run ```
$ xinput list-props "Atmel Atmel maXTouch Digitizer"
Device 'Atmel Atmel maXTouch Digitizer':
	Device Enabled (128):	1
	Coordinate Transformation Matrix (130):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (249):	0
	Device Accel Constant Deceleration (250):	1.000000
	Device Accel Adaptive Deceleration (251):	1.000000
	Device Accel Velocity Scaling (252):	10.000000
	Device Product ID (245):	1003, 33809
	Device Node (246):	"/dev/input/event4"
	Evdev Axis Inversion (282):	0, 0
	Evdev Axis Calibration (283):	<no items>
	Evdev Axes Swap (284):	0
	Axis Labels (285):	"Abs MT Position X" (280), "Abs MT Position Y" (281), "Abs MT Touch Major" (277), "Abs MT Touch Minor" (278), "Abs MT Orientation" (279), "None" (0), "None" (0)
	Button Labels (286):	"Button Unknown" (276), "Button Unknown" (276), "Button Unknown" (276), "Button Wheel Up" (134), "Button Wheel Down" (135)
	Evdev Middle Button Emulation (287):	0
	Evdev Middle Button Timeout (288):	50
	Evdev Third Button Emulation (289):	1
	Evdev Third Button Emulation Timeout (290):	750
	Evdev Third Button Emulation Button (291):	3
	Evdev Third Button Emulation Threshold (292):	20
	Evdev Wheel Emulation (293):	0
	Evdev Wheel Emulation Axes (294):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (295):	10
	Evdev Wheel Emulation Timeout (296):	200
	Evdev Wheel Emulation Button (297):	4
	Evdev Drag Lock Buttons (298):	0
```

But it doesn't work. I can touch the same spot on my screen all day and nothing happens. Not sure if this is specific to my touchscreen, or evdev in general... I have the new Samsung XE700T1C with the Atmel maXTouch Digitizer, which I believe is the same touchscreen that's on the previous Series 7 Slate (XE700T1A).

What could be going on here? For what it's worth, if I enable third button emulation on my touchpad and hold down the left-click button, THAT works... but not with my touch SCREEN... so maybe it's my model or driver.

I filed a bug for this here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1084938](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1084938)

---

