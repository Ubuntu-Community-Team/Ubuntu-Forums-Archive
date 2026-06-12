---
title: "Removing mouse acceleration?"
date: 2016-07-08
forum: General Help
---

### Post by infernouk on 2016-07-08
Hey guys

I am getting annoyed with Ubuntu's mouse acceleration as a new user.

Is there a way to disable it? Ive googled but cant find anything up to date that works!

Thanks for any tips

---

### Post by DuckHook on 2016-07-08
Upper right gear icon > System Settings > Mouse & Touchpad > Mouse > Slide "Pointer speed" bar all the way left to "0"

---

### Post by infernouk on 2016-07-09
> **DuckHook said:**
> Upper right gear icon > System Settings > Mouse & Touchpad > Mouse > Slide "Pointer speed" bar all the way left to "0"

that affects pointer speed and not acceleration

---

### Post by DuckHook on 2016-07-09
Open a terminal and do:```
xinput list
```My output looks as follows, but yours will differ:```
duckhook@Computer:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Desktop® 1.00	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft Wireless Optical Desktop® 1.00	id=8	[slave  keyboard (3)]
```Yours will look different unless you have exactly my equipment, which is unlikely. You wish to identify the id# for your pointing device. In my case it is id=9. Note this number. Then, to make sure that you have proper device ID'd, do:```
xinput list-props n
```...replacing "n" with the id number that you just identified. Result should look similar to the following:```
duckhook@Computer:~$ xinput list-props 9
Device 'Microsoft Microsoft Wireless Optical Desktop® 1.00':
	Device Enabled (143):	1
	Coordinate Transformation Matrix (145):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (294):	0
	Device Accel Constant Deceleration (295):	1.000000
	Device Accel Adaptive Deceleration (296):	1.000000
	Device Accel Velocity Scaling (297):	10.000000
	Device Product ID (285):	1118, 1957
	Device Node (286):	"/dev/input/event3"
	Evdev Axis Inversion (298):	0, 0
	Evdev Axes Swap (300):	0
	Axis Labels (301):	"Rel X" (153), "Rel Y" (154), "Rel Horiz Wheel" (291), "Rel Dial" (292), "Rel Vert Wheel" (293)
	Button Labels (302):	"Button Left" (146), "Button Middle" (147), "Button Right" (148), "Button Wheel Up" (149), "Button Wheel Down" (150), "Button Horiz Wheel Left" (151), "Button Horiz Wheel Right" (152), "Button Side" (289), "Button Extra" (290), "Button Unknown" (288), "Button Unknown" (288), "Button Unknown" (288), "Button Unknown" (288)
	Evdev Scrolling Distance (303):	1, 1, 1
	Evdev Middle Button Emulation (304):	0
	Evdev Middle Button Timeout (305):	50
	Evdev Third Button Emulation (306):	0
	Evdev Third Button Emulation Timeout (307):	1000
	Evdev Third Button Emulation Button (308):	3
	Evdev Third Button Emulation Threshold (309):	20
	Evdev Wheel Emulation (310):	0
	Evdev Wheel Emulation Axes (311):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (312):	10
	Evdev Wheel Emulation Timeout (313):	200
	Evdev Wheel Emulation Button (314):	4
	Evdev Drag Lock Buttons (315):	0

```If your output doesn't look similar to this, then you have identified the wrong device. Try another ID until you get this output. We are especially interested in seeing the line:```
Device Accel Profile (294):	0
```To turn off acceleration, we want to load profile "-1". To test this temporarily, do:```
xinput set-prop n "Device Accel Profile" -1
```...where "n" is replaced with your device ID. Changed behaviour should take effect immediately. Test your mouse movement to see if this has desired effect. **Note to others who may happen upon this thread**: these instructions disable acceleration altogether, as per OP's request. To *reduce* acceleration that may be too aggressive (but keep it enabled), do not touch "Device Accel Profile". Instead, increase the value of Device Accel Constant Deceleration". Example:```
xinput set-prop 9 "Device Accel Constant Deceleration" 3
```The number (in my example, "3") acts roughly as the denominator in a function that reduces acceleration. Hence, the larger the number, the less aggressive the acceleration. The default is 1 and cannot go lower. Play around with this number until you get the acceleration that you want.

To make the change permanent, we must define a script that is loaded at login. If you do not have a ~/bin directory, make one:```
mkdir ~/bin
```Then create file with some meaningful name. e.g.:```
nano ~/bin/mouse_accel.sh
```Add following content to new file:```
#! /bin/bash

#This setting disables mouse acceleration at login. Created by user on 2016-07-09
xinput set-prop n "Device Accel Profile" -1
```Make file executable with:```
chmod 751 ~/bin/mouse_accel.sh
```To start this script at login, add it to your Startup Applications.

For detailed explanation of xorg acceleration parameters: [https://www.x.org/wiki/Development/Documentation/PointerAcceleration/](https://www.x.org/wiki/Development/Documentation/PointerAcceleration/)

---

### Post by wamwung on 2016-10-31
Hi Duck Hook,

I did all the steps as you said and it almost worked flawlessly. After my restart, as soon as I login I see the acceleration is disabled but in a few seconds the acceleration is turned it on again. 

Do you have any idea what is happening? (I'm using Ubuntu 16.04 LTS)

Thank you,

---

### Post by wamwung on 2016-11-11
> **wamwung said:**
> Hi Duck Hook,

I did all the steps as you said and it almost worked flawlessly. After my restart, as soon as I login I see the acceleration is disabled but in a few seconds the acceleration is turned it on again. 

Do you have any idea what is happening? (I'm using Ubuntu 16.04 LTS)

Thank you,

I've saved the mouse_accel.sh in my /home folder and it worked now! Thank you,

---

