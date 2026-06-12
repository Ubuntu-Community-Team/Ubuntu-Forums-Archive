---
title: "synaptics driver intermittent"
date: 2007-03-22
forum: General Help
---

### Post by Charles Hand on 2007-03-22
I have this section in my xorgs.conf file:

```

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "SHMConfig" "1"
    Option         "MinSpeed" "0.3"
    Option         "MaxSpeed" "1.0"
    Option         "AccelFactor" "0.07"
    Option         "LeftEdge" "0"
    Option         "TopEdge" "0"
    Option         "RightEdge" "950"
#    Option         "BottomEdge" "650"
    Option         "BottomEdge" "800"
    Option         "VertScrollDelta" "30"
    Option         "HorizScrollDelta" "30"
    Option         "RTCornerButton" "0"
    Option         "LTCornerButton" "0"
    Option         "RBCornerButton" "0"
    Option         "LBCornerButton" "0"
    Option         "PalmDetect" "1"
EndSection

```

Under dapper, the Alps/Synaptics touchpad worked all the time and because of the SHMConfig option, I could adjust parameters using synclient as well.

Under Edgy the synaptics driver is intermittent from boot to boot. Half the time it works normally, half the time it acts as if this section were not in xorgs.conf: scrolling doesn't work, synclient doesn't work...

I don't see anything about why it is failing in Xorg.0.log, messages or syslog.

---

### Post by Charles Hand on 2007-03-23
I tried changing it to Alps Touchpad on /dev/input/event5 according to /proc/bus/input/devices, and the behavior is unchanged.

It is as if with a 50% prbability that whole section of xorg.conf gets skipped when the xserver starts.

---

### Post by Charles Hand on 2007-03-24
When I run synclient, it does not complain about no shared memory. So the shared memory is being set up somehow and synclient can attach to the shared memory. But synclient can't affect any changes to the touchpad behaviour, and synclient -m 10 doesn't show any events.

---

### Post by Charles Hand on 2007-03-24
When I cold boot, it doesn't work. When I restart the X server it does work.

---

### Post by Charles Hand on 2007-04-02
The first time I log into a KDE session through gdm (and even before I log in, while sitting at the gdm screen), I get:

> (--) Synaptics Touchpad auto-dev sets device to /dev/input/event2


and the touchpad acts like a dumb mouse

After logging out of the KDE session, and forever more until I reboot, I get:

> (--) Synaptics Touchpad auto-dev sets device to /dev/input/event5

and the touchpad acts like an Alps (Synaptics, whatever) touchpad.

As if auto-dev is confused before first time I log in, but gets unconfused when I log out once.

---

### Post by Charles Hand on 2007-04-02
This appears to be the same problem as this:
[http://ubuntuforums.org/showthread.php?t=375027](http://ubuntuforums.org/showthread.php?t=375027)

I have corrected the behavior by altering xorg.conf thusly in the Synaptics InputDevice section:

```
#	Option		"Device"		"/dev/psaux"
	Option		"Device"		"/dev/input/mouse1"
#	Option		"Protocol"		"auto-dev"
	Option		"Protocol"		"auto"

```

I have no idea why it works. I got it from here:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

---

### Post by Charles Hand on 2007-04-03
The fix was only temporary. It's still intermittent.

---

### Post by Charles Hand on 2007-04-03
It's a well-known Edgy bug
#69152

---

