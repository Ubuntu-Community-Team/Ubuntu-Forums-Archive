---
title: "Xgl gives distorted graphics"
date: 2007-11-19
forum: General Help
---

### Post by BunsenBurner on 2007-11-19
I am running Gutsy on a IBM T43 (ATI X300) and until today I've been running 'xgl - compiz-fusion - fglrx' without any problems (i.e. for about 2 weeks). Booting the computer today, having it turned off since Friday (when everything worked fine), i get distorted graphics!

This is what I've done: 
* On Friday I updated fglrx (2.6.22.4_14.9 to _14.10). Actually I downloaded all upgrades.
* Today I booted and got all kinds of strange artifacts in the graphics, making it impossible to see anything (but only if I move windows, scroll inside windows and other events that include movement. Leaving an opened window static I only see minor distortions)
* I reversed to previous fglrx driver and rebooted -> same problem
* I re-installed xgl and rebooted -> same problem
* Uninstalled xgl (and thereby also compiz-fusion) and rebooted -> problem gone!
* Updated to latest fglrx drivers again and rebooted -> no problems!
* Problem is: I like compiz-fusion and cannot understand why it's not working today, when it worked flawlessly (as far as I know :)) on Friday. I get a feeling it has something to do with xgl, since all looks fine when it's not installed. 

Anyone experienced the same problems or got any ideas?

Regards, 

Thomas

---

### Post by mali2297 on 2007-11-19
If you have ATI X300, you should be able to use the radeon driver with AIGLX as an alternative to fglrx with XGL. See this howto:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If it works, you can run Compiz Fusion directly (no special session).

---

### Post by BunsenBurner on 2007-11-20
Thanks for your reply.

I followed the howto and got compiz-fusion started (wohoo!), but unfortunately it doesn't work for long. Trying to get the setup back to what I had (cube with 4 sides, skydome etc) makes the computer lockup and I have to power off with the power button.

Actually activating the cube doesn't even work, and it's when I try to spin it, everything locks up.

EDIT: It's really selecting an area on the desktop (mouse-left-click-and-hold and drag. Then releasing the mouse button) it locks up.

---

### Post by tors on 2007-11-22
Anyone else having these hardware locking-problems when using X300 and the open source drivers with AIGLX?

How does it run if you don't start Compiz? Does it still freeze?

---

### Post by BunsenBurner on 2007-11-22
Currently I run with Visual Effects set to "None" (under Appearence > Preferences) and I have no lock-ups.

Two new "phenomena" have appeared though:

1) The gnome panels don't cover the whole width of my external monitor (1680x1050), only 1440 (laptop settings). Can't understand why

2) Opening the laptop lid, turns the monitor off and completely locks the laptop screen, in a way that I need to restart the computer using the power button :S

I'm starting to think "re-install the damn thing"

/Thomas

---

