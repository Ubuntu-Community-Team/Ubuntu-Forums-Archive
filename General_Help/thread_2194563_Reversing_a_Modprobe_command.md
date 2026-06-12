---
title: "Reversing a Modprobe command"
date: 2013-12-19
forum: General Help
---

### Post by wewantutopia on 2013-12-19
Hello, I was having an issue with my laptop touchpad where my right click suddenly stopped woring.  After some searching I discovered a solution but it broke some other touchpad functionality.

These are the commands I used:

```

sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot
```

How can I reverse this?

Thank you!!

---

### Post by steeldriver on 2013-12-19
You can just remove the /etc/modprobe.d/psmouse.modprobe file and reboot again

---

### Post by tgalati4 on 2013-12-19
Open a terminal:

```
modinfo psmouse
```

It might look like:

tgalati4@Mint14-Extensa ~ $ modinfo psmouse
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/input/mouse/psmouse.ko
license:        GPL
description:    PS/2 mouse driver
author:         Vojtech Pavlik <vojtech@suse.cz>
srcversion:     986B270094FBC3368FA83BC
alias:          serio:ty05pr*id*ex*
alias:          serio:ty01pr*id*ex*
depends:        
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 
parm:           cy_debug:Set CyPS/2 debug output level (0, 1, or 2) (int)
parm:           cy_read_timeout:Set CyPS/2 cmd read timeout (default 200 msec) (int)
parm:           proto:Highest protocol extension to probe (bare, imps, exps, any). Useful for KVM switches. (proto_abbrev)
parm:           resolution:Resolution, in dpi. (uint)
parm:           rate:Report rate, in reports per second. (uint)
parm:           smartscroll:Logitech Smartscroll autorepeat, 1 = enabled (default), 0 = disabled. (bool)
parm:           resetafter:Reset device after so many bad packets (0 = never). (uint)
parm:           resync_time:How long can mouse stay idle before forcing resync (in seconds, 0 = never). (uint)


You can manually load the module with different options.  You don't need to reboot.  You might need to logout of the desktop and log back in again.

Post the output of your current settings:

```
cat /etc/modprobe.d/psmouse.modprobe
```

What is the model of the laptop?  For a Samsung, there are several switches to play with:  [https://help.ubuntu.com/community/SamsungSeries9#Clickpad](https://help.ubuntu.com/community/SamsungSeries9#Clickpad)

---

### Post by wewantutopia on 2013-12-19
Ok, I deleted /etc/modprobe.d/psmouse.modprobe and I have a touchpad tab in mouse and touchpad.  I also have 2 finger scrolling back, BUT I'm back to no right click (which worked fine with psmouse)

I can't cat /etc/modprobe.d/psmouse.modprobe becasue I just deleted it.

I have a Samsung Series 7 NP700Z5A-S0AUS running 12.04

Any ideas how to get right click back?  I'm not sure why it stopped to begin with.

---

### Post by wewantutopia on 2013-12-19
Here is the output from modinfo psmouse

```
filename:       /lib/modules/3.5.0-44-generic/kernel/drivers/input/mouse/psmouse.ko
license:        GPL
description:    PS/2 mouse driver
author:         Vojtech Pavlik <vojtech@suse.cz>
srcversion:     986B270094FBC3368FA83BC
alias:          serio:ty05pr*id*ex*
alias:          serio:ty01pr*id*ex*
depends:        
intree:         Y
vermagic:       3.5.0-44-generic SMP mod_unload modversions 686 
parm:           cy_debug:Set CyPS/2 debug output level (0, 1, or 2) (int)
parm:           cy_read_timeout:Set CyPS/2 cmd read timeout (default 200 msec) (int)
parm:           proto:Highest protocol extension to probe (bare, imps, exps, any). Useful for KVM switches. (proto_abbrev)
parm:           resolution:Resolution, in dpi. (uint)
parm:           rate:Report rate, in reports per second. (uint)
parm:           smartscroll:Logitech Smartscroll autorepeat, 1 = enabled (default), 0 = disabled. (bool)
parm:           resetafter:Reset device after so many bad packets (0 = never). (uint)
parm:           resync_time:How long can mouse stay idle before forcing resync (in seconds, 0 = never). (uint)


```

---

### Post by tgalati4 on 2013-12-19
Try some of the suggestions in the link that I provided for Samsung Series9.  It might work.

---

