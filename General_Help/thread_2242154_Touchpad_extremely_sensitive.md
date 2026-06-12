---
title: "Touchpad extremely sensitive"
date: 2014-08-30
forum: General Help
---

### Post by dorlow on 2014-08-30
I just installed Ubuntu 14.04.  It's working great except the touchpad is extremely sensitive.  It seems like the cursor moves exactly where I want it to.  But as soon as I lift my finger, the cursor just jumps random places a few inches off.  Takes forever to click what I want to click.  Any ideas how to fix this?

---

### Post by gdesilva on 2014-08-30
Go to Settings -> Mouse and Touch Pad and here you can adjust the values for sensitivity and accelleration etc.

---

### Post by TBerk on 2014-08-30
Im having similar trouble.

In my case I'm running Ubuntu Studio 14.04 and  a very small Gear Head KB3700TP keyboard.

My initial searches first turned up hits like "All your troubles go away if you install gsynaptics" only to find out it's not supported any more.

Then I found out it's been replaced w/ gpointing-device-settings.  Buuuuut that crashes on my system.  

When installed and working correctly it places an icon in Settings' Manager called Pointing Devices.

Perhaps installing gpointing-device-settings, if currently missing, will help in your case.

PS- The Mouse and Touchpad settings manager, in my case, has only USB Keyboard options, nothing Trackpad specific.

---

### Post by dorlow on 2014-08-31
> **gdesilva said:**
> Go to Settings -> Mouse and Touch Pad and here you can adjust the values for sensitivity and accelleration etc.

I've already been messing around with these settings.  I've noticed some articles say it should have separate settings for touchpad vs mouse.  Mine doesn't.

---

### Post by wn1ytw on 2014-08-31
some good advice on touchpad issues can be found here:  [http://ubuntuforums.org/showthread.php?t=1419833](http://ubuntuforums.org/showthread.php?t=1419833)

---

### Post by dorlow on 2014-09-10
I've been using the commands to try and get it right and not figuring it out.  I can't figure out what option would fix my issue.  My touchpad works perfect when moving it, until I lift my finger off the mousepad.  As I lift my finger off the mousepad, it jumps in random directions. Here are the options I have...

david@david-laptop:~$ xinput list-props "SynPS/2 Synaptics TouchPad"
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (263):	1
	Device Accel Constant Deceleration (264):	5.000000
	Device Accel Adaptive Deceleration (265):	1.000000
	Device Accel Velocity Scaling (266):	12.500000
	Synaptics Edges (287):	1766, 5390, 1649, 4621
	Synaptics Finger (288):	25, 30, 0
	Synaptics Tap Time (289):	180
	Synaptics Tap Move (290):	239
	Synaptics Tap Durations (291):	180, 180, 100
	Synaptics ClickPad (292):	0
	Synaptics Middle Button Timeout (293):	75
	Synaptics Two-Finger Pressure (294):	282
	Synaptics Two-Finger Width (295):	7
	Synaptics Scrolling Distance (296):	108, 108
	Synaptics Edge Scrolling (297):	1, 1, 0
	Synaptics Two-Finger Scrolling (298):	0, 0
	Synaptics Move Speed (299):	1.000000, 1.750000, 0.050000, 0.000000
	Synaptics Off (300):	0
	Synaptics Locked Drags (301):	0
	Synaptics Locked Drags Timeout (302):	5000
	Synaptics Tap Action (303):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (304):	1, 1, 0
	Synaptics Circular Scrolling (305):	0
	Synaptics Circular Scrolling Distance (306):	0.100000
	Synaptics Circular Scrolling Trigger (307):	0
	Synaptics Circular Pad (308):	0
	Synaptics Palm Detection (309):	0
	Synaptics Palm Dimensions (310):	10, 200
	Synaptics Coasting Speed (311):	20.000000, 50.000000
	Synaptics Pressure Motion (312):	30, 160
	Synaptics Pressure Motion Factor (313):	1.000000, 1.000000
	Synaptics Resolution Detect (314):	1
	Synaptics Grab Event Device (315):	1
	Synaptics Gestures (316):	1
	Synaptics Capabilities (317):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (318):	92, 47
	Synaptics Area (319):	0, 0, 0, 0
	Synaptics Noise Cancellation (320):	8, 8
	Device Product ID (252):	2, 7
	Device Node (253):	"/dev/input/event6"
david@david-laptop:~$ 


I modified [COLOR=#000000][FONT=Arial]Device Accel Constant Deceleration from default of 5.0 to 4.0 and it seemed to help a little.  I first started at 2.5 and it was way too low.  But the symptoms I have, I can't think of an option that would fix it.  It never happened in Windows no matter what option I have.  [/FONT][/COLOR]

---

### Post by dorlow on 2014-09-10
Only thing I can think is there has to be an option for how much pressure is needed to move the cursor.  I think what is happening is the touchpad moves with the slightest touch of the pad.  In Windows, it took more pressure to move it which is why the cursor didn't jump.  When I'm lifting my finger to type, that slight brush of my finger probably not quite touching the pad is causing it to jump.  Or my finger leaving the mousepad is being processed as the last point of my finger touching it is processed as moving in a direction.

---

