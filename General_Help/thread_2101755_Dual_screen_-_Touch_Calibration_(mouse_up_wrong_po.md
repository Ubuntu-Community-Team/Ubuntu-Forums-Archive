---
title: "Dual screen - Touch Calibration (mouse up wrong position)"
date: 2013-01-05
forum: General Help
---

### Post by plo on 2013-01-05
I posted on this topic in september but no one replied so I am now trying again.
I have a very annoying problem preventing me from using my
touchscreen.
I'm using 12.04 (64-bit) and have a dualscreen setup. Touch is working but scales to both screens as default.
To fix this I set:

xinput set-prop 10 --type=float "Coordinate Transformation Matrix" 0.5 0 0 0 1 0 0 0 1

Now mouse down positions correctly BUT mouse up is reported 50% to the left.

output of "xinput test 10"   
button press   1 a[0]=760 a[1]=643 
button release 1 a[0]=380 a[1]=643 

With standard / no transformation Matrix I get
button press   1 a[0]=829 a[1]=361 
button release 1 a[0]=829 a[1]=361

Note. If I disconnect the second monitor (tv) touch works perfect.

On earlier versions (and different touch screen) I was able to set the input device to only work on sreen 0 and ignore the second screen but currently it does not work when I set up separate X-screens in nvidia-settings. 

Output of "xinput list-props 10"

[I]Device 'Acer T231H':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	0.500000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (264):	0
	Device Accel Constant Deceleration (265):	1.000000
	Device Accel Adaptive Deceleration (266):	1.000000
	Device Accel Velocity Scaling (267):	10.000000
	Device Product ID (260):	1032, 12289
	Device Node (261):	"/dev/input/event6"
	Evdev Axis Inversion (268):	0, 0
	Evdev Axis Calibration (269):	0, 1920, 0, 1080
	Evdev Axes Swap (270):	0
	Axis Labels (271):	"Abs MT Position X" (287), "Abs MT Position Y" (288), "None" (0), "None" (0)
	Button Labels (272):	"Button Unknown" (263), "Button Unknown" (263), "Button Unknown" (263), "Button Wheel Up" (148), "Button Wheel Down" (149)
	Evdev Middle Button Emulation (273):	0
	Evdev Middle Button Timeout (274):	50
	Evdev Third Button Emulation (275):	0
	Evdev Third Button Emulation Timeout (276):	1000
	Evdev Third Button Emulation Button (277):	3
	Evdev Third Button Emulation Threshold (278):	20
	Evdev Wheel Emulation (279):	0
	Evdev Wheel Emulation Axes (280):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (281):	10
	Evdev Wheel Emulation Timeout (282):	200
	Evdev Wheel Emulation Button (283):	4
	Evdev Drag Lock Buttons (284):	0[/I]

Anyone, or if you can point me to a better place for help??

---

### Post by crs4vic on 2013-04-03
Hi,
I have exactly the same problem.
Could you solve yours?
Thanks

---

### Post by plo on 2013-04-03
> **crs4vic said:**
> Hi,
I have exactly the same problem.
Could you solve yours?
Thanks

Unfortunately not. I have not looked at it for a long while - sometimes one just have to accept once fate. :(

I found this  [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)  and also tables for supported devices [http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html).
Though that is for multitouch, I thought they might have the knowledge to help. I did email them but received no answer. Maybe you could try contacting them?

What surprises me most is that no one has replied with any hint of solution at all. Maybe I posted in wrong forum.
Have you tried somewhere else???

---

### Post by crs4vic on 2013-04-04
Hi plo,

thanks for your reply.
I have two full-HD monitors, the one on the left is a touchscreen. Nvidia twinview is enabled and I set the touchscreen input via xinput
(my dev id is 11):

xinput set-prop 11 "Coordinate Transformation Matrix" 0.5 0.0 0.0 0 1.0 0.0 0.0 0.0 1

If I check the xinput settings everything is OK:
# xinput list-props 11 | grep Coord
    Coordinate Transformation Matrix (144):    0.500000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000

The touchscreen apparently works fine (the mouse cursor tracks my finger), but the "mouse release" event has wrong coordinates...
so, I'm stuck with this issue, just like you!

Does nobody else here know the answer?

I let you know if I solve it.

---

### Post by crs4vic on 2013-04-04
I've just found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1015183](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1015183)

---

