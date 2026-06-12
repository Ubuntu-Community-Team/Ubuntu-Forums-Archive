---
title: "ATI driver for Sun UltraSPARC IIIi"
date: 2008-05-03
forum: General Help
---

### Post by Verdin on 2008-05-03
I'm unable to enable the restricted modules through the terminal and I can't find any ATI drive for UltraSPARC on AMDs website.  All they have is x86 and x86-64 drivers for linux.  I have a 32 bit PCI graphics card with [COLOR="Red"]Radeon RV100 QZ [Radeon 7000/VE][/COLOR] chipset.  I guess fglrx won't work with it anyway.

Anyone have any ideas about how I could get this graphics card to work?  I can't get any GUI at all!

Thanks..

---

### Post by howlingmadhowie on 2008-05-04
i think getting the card to work under linux will be pretty impossible, unless ati has produced a driver (which is extremely unlikely). the card however should also support vesa, so try using the standard vesa driver in /etc/X11/xorg.conf and seeing what /var/log/Xorg.0.log has to say about it. that's all i can suggest, unfortunately.

---

### Post by Verdin on 2008-05-04
I've tried reconfiguring:
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

and just get the error:
FATAL:  Module battery not found

I have no idea what this means.

I ran the /var/log/Xorg.0.log but don't know what to look for.

---

### Post by howlingmadhowie on 2008-05-05
> **Verdin said:**
> I've tried reconfiguring:
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

and just get the error:
FATAL:  Module battery not found

I have no idea what this means.

I ran the /var/log/Xorg.0.log but don't know what to look for.


the /var/log/Xorg.0.log will contain the messages from the xserver when it last tried to start. probably at the end of the file there will be some error messages.

i don't see why a missing battery module should stop the xserver-xorg package from being reconfigured. i suspect a problem elsewhere.

---

### Post by balkor on 2008-05-29
I think I am having the same issue with my SPARC
SunFire 280R
(2) UltraSPARC III+ (cheetah+)
ATI Technologies Radeon 7000/ve RV100qy


/etc/gdm/failsafeXServer: line 47: [: too many arguments
Warning:  Could not retrieve EDID because get-edid is not installed (1)
Warning:  Could not retreive PCI IDs because discover is not installed (1)
FATAL: Module battery not found.
: error: this program does not know how to configure the "10
shared/default-x-server doesn't exist" X server
Warning:  Could not generate /etc/X11/xorg.conf.failsafe for vesa driver
/var/log/gdm/:0.log (END)

---

