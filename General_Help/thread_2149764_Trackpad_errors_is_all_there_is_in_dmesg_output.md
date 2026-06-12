---
title: "Trackpad errors is all there is in dmesg output"
date: 2013-05-29
forum: General Help
---

### Post by Andres Gonzalez on 2013-05-29
I have a Dell XPS Developer Edition running 12.4, all stock.  In the Mouse and Touchpad, I have tried to disable the Touchpad but the only option Unity gives me is "Disable touchpad while typing"  I want to completely disable it but it appears that this does not.

When I do dmesg, all I get is many screen fulls of this:

[ 3725.435970] psmouse serio1: Trackpad at isa006-/serio1/input- lost sync at byte 1
[ 3725.447755] psmouse serio1: Trackpad at isa006-/serio1/input- - driver resynced.

Thats all I get, none of the typical output from dmesg.

Anyone know what is going on here?

-Andres

---

### Post by wildmanne39 on 2013-05-29
*Thread moved to **General Help**.*

---

### Post by tgalati4 on 2013-05-30
Is there an option in BIOS to turn off the touchpad?

These are the switches available for the psmouse driver (in 12.10):

tgalati4@Mint14-Extensa ~ $ modinfo psmouse
filename:       /lib/modules/3.5.0-27-generic/kernel/drivers/input/mouse/psmouse.ko
license:        GPL
description:    PS/2 mouse driver
author:         Vojtech Pavlik <vojtech@suse.cz>
srcversion:     A6C6EC86EC49DACDCD43A4D
alias:          serio:ty05pr*id*ex*
alias:          serio:ty01pr*id*ex*
depends:        
intree:         Y
vermagic:       3.5.0-27-generic SMP mod_unload modversions 
parm:           cy_debug:Set CyPS/2 debug output level (0, 1, or 2) (int)
parm:           cy_read_timeout:Set CyPS/2 cmd read timeout (default 200 msec) (int)
parm:           proto:Highest protocol extension to probe (bare, imps, exps, any). Useful for KVM switches. (proto_abbrev)
parm:           resolution:Resolution, in dpi. (uint)
parm:           rate:Report rate, in reports per second. (uint)
parm:           smartscroll:Logitech Smartscroll autorepeat, 1 = enabled (default), 0 = disabled. (bool)
parm:           resetafter:Reset device after so many bad packets (0 = never). (uint)
parm:           resync_time:How long can mouse stay idle before forcing resync (in seconds, 0 = never). (uint)

---

