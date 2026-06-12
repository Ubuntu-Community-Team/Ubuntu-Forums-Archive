---
title: "Gutsy + nvidia 6150 + stop X = blank screen of colour"
date: 2007-12-12
forum: General Help
---

### Post by ardnut on 2007-12-12
I've installed ubuntu gutsy server on a m2npv-vm mobo with onboard nvidia 6150.  It's being used as a dedicated MythTV box, so I've set it to auto login the mythtv user and start a X session (via .xinitrc with ratposion as the WM).  Everything works great and I'm using the latest stable nvidia driver (not nv) ubuntu comes with.

The problem I'm getting is that I can not quit X, or ctrl+alt+f1, etc... to other terminals.  If I try then the whole screen just blanks to a single colour, mainly either bright blue/green/red/pink, it's different each time.  The machine is still running fine, I can ssh in without issue, but it's as if X has froozen and the nvidia driver just spits out a blank screen full of some colour in its buffer.  I see the same thing occur when I shut the machine down and it stops X.

Any idea what would cause this? or where I could hunt down the prob?  the X, dmesg, messages and syslog logs show no obvious errors.  I've tried searching for a solution, but it's really difficult thing to search for.

Thanks,
Ash

---

