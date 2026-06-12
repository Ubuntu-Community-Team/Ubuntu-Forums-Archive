---
title: "Ubuntu loading dots freeze?"
date: 2014-03-22
forum: General Help
---

### Post by david-sy6 on 2014-03-22
This isn't a major issue, but I just wanted to know why this is happening.
Basically, you know when you load up Ubuntu and the splash screen appears with the word "Ubuntu" and the dots start filling up? Well mine used to fill up as normal while the computer loaded, but now they just suddenly go from 1 dot to all dots filled and freeze that way. The computer didn't start up at all when this happened at first, turned out I had to reconfigure Xserver Xorg or something like that, the computer does load up now, but yeah I'm just wondering why on earth my dots aren't filling like they should.

Sorry this is probably the stupidest question you've ever had :$

---

### Post by grahammechanical on 2014-03-22
A new competition is about to start. "The stupidest question ever asked on the forum." :) Just joking.

It is a splash screen. It does two things. 1) it hides the system messages that Linux normally prints to the screen as it loads. 2) The moving dots reassure us that the OS is actually loading and the computer has not stopped working.

My guess is that in case like this Linux gets distracted by a problem reading configuration files. There may be conflicting settings. Linux may be trying again and again to load some module or set up some configuration setting.

I would go further and guess that this has something to do with that reconfiguration of Xserver Xorg. In newer versions of Ubuntu the Xserver will get the monitor screen resolution settings directly from the monitor if it is a digital and not a CRT monitor.

Linux reads the Extended Display Identification Data (EDID) directly from the monitor and not from a configuration script. This is why we do not need to put in monitor resolution settings when we install Ubuntu. Now, the Xserver may have difficulty reading the EDID. That happened to me once when my graphic adapter overheated. Or it may be experiencing a conflict if it is trying to both read the EDID and a configuration script.

Regards.

---

### Post by Iowan on 2014-03-22
> **grahammechanical said:**
> Linux reads the Extended Display Identification Data (EDID) directly from the monitor and not from a configuration script. This is why we do not need to put in monitor resolution settings when we install Ubuntu. Now, the Xserver may have difficulty reading the EDID. That happened to me once when my graphic adapter overheated. Or it may be experiencing a conflict if it is trying to both read the EDID and a configuration script...Hmmm...
Maybe my KVM switch is causing some of my bootup screen problems...
(Sorry... back on topic, now.)

---

