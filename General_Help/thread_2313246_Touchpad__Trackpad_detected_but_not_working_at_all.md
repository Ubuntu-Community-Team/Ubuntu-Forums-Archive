---
title: "Touchpad / Trackpad detected but not working at all"
date: 2016-02-10
forum: General Help
---

### Post by james197 on 2016-02-10
Hi all,


Just booted into Ubuntu MATE 15.10 64bit on a live usb on my Dell 3452 with the intention of then installing it but the touchpad isn't working at all. So I've plugged in my USB mouse and that works OK. I found the following on google to check if it's being detected, and it seems to be. Any ideas? I mainly need the laptop for out and about so can't really use the USB mouse.


> cat /proc/bus/input/devices 



brings up:


>     I: Bus=0011 Vendor=0002 Product=0007 Version=01a1
    N: Name="SynPS/2 Synaptics TouchPad"
    P: Phys=isa0060/serio1/input0
    S: Sysfs=/devices/platform/i8042/serio1/input/input7
    U: Uniq=
    H: Handlers=mouse0 event6 
    B: PROP=5
    B: EV=b
    B: KEY=e520 610000 0 0 0 0
    B: ABS=660800011000003


---

### Post by Desert_Outlaw on 2016-03-24
Were you ever able to resolve the issue or does it still persist. I have similar issue.

---

### Post by montag dp on 2016-03-24
What's the output of:

```
xinput
```

If you see SynPS/2 Synaptics Touchpad, post the output of this:

```
xinput list-props "SynPS/2 Synaptics TouchPad"
```

---

