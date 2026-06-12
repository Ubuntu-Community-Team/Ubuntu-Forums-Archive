---
title: "Alps Touchpad"
date: 2014-02-10
forum: General Help
---

### Post by Cory_C on 2014-02-10
Hello,

I have been attempting to enable two-finger scrolling (or scrolling of any sort) on my distribution. I have updated the driver to version 1.3. When I click the two finger scroll button, and click back into settings, it is as if I had never pushed the button to begin with.
Any help would be appreciated.

---

### Post by tgalati4 on 2014-02-10
Does your Alps touchpad support 2-finger?

Open a terminal and post the output of:

```
grep touchpad /var/log/Xorg.0.log
```

also

```
sudo tpconfig -i
```

It might look like:

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;		no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

And from this I just learned that I have right-button-click by tapping on the lower right corner.

My 2-finger scrolling worked out-of-the-box.  Otherwise you would set some switches in /etc/X11/xorg.conf as follows:


#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#	Option		"VertTwoFingerScroll"	"1"
#	Option		"HorizTwoFingerScroll"	"1"
#EndSection

Any changes to the xorg system requires either a reboot or a logout/login for them to take effect.

---

