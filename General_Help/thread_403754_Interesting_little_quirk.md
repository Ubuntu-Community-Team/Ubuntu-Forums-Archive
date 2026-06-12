---
title: "Interesting little quirk"
date: 2007-04-07
forum: General Help
---

### Post by FretFire on 2007-04-07
I recently installed Ubuntu on a second hard drive in a dual boot configuration.  I've got my video card drivers installed, Cedega is up and running so I can play City of Heroes (can you tell my priorities?), and everything is gravy.  For the most part.

After the machine sits idle for 20 minutes or so my mouse and keyboard stop responding.  I turned off the screensaver last night and watched it to see if the machine fully locked up or not.  I had a download running, and it kept going without issue even after I was unable to move my mouse or Ctrl+Alt+Backspace to log out, so it doesn't seem to be hanging up.  My mouse and keyboard are both USB, so I'm thinking maybe Ubuntu stops listening to my USB ports once my machine goes to “sleep”.  Does this sound feasible?  I'm using the 2.6.17-11 kernel, and I'll list my machine details below.  Any tips are greatly appreciated.  I'm comfortable in Linux though I cut my teeth on Fedora and RHEL, and I'm really enjoying Ubuntu so far.  I've got it running solo on my laptop without any trouble.

AMD Athlon(TM)64 X2 3800+
250GB SATA-II HDD (For Linux partitions)
Asus M2N32-SLI Deluxe motherboard
2GB PC6400 DDR2/800 RAM

FWIW, The mouse/keyboard are plugged into USB ports on the motherboard.

---

### Post by FretFire on 2007-04-07
Ok I'm definitely thinking this has to do with Ubuntu dismissing the USB ports when my machine goes to sleep.  I let it site idle again today, but this time I plugged in a PS/2 keyboard once it became unresponsive and a keystroke brought the monitor back, but my USB mouse/keyboard were still unusable.  Do I need to declare these as USB devices in xorg.conf or something?  I tried setting the mouse as USB there but X didn't like that and wouldn't start up properly, maybe I had the syntax wrong?

---

