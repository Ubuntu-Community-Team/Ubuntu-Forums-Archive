---
title: "Crash and presumably faulty hardware (I think)"
date: 2007-05-12
forum: General Help
---

### Post by endrre on 2007-05-12
I'm experiencing some weird problem with my system. On the box i have both linux and windows installed, and the problem appears in both of the systems. 

The crashes are completely random, sometimes I can run the system for days without it happen, or sometimes it can be just a few hours between each crash. 
The difference is that while windows crashes completely (just hangs, no bsod), linux is somewhat softer on that spot: I think it looks like linux is "losing" memory, i.e. I can't start programs, just stop them. Sometimes I can observe when a crash is commencing, for example that the wireless network card stops working. Before some time passes by, I can manage to shut down the box normally and unmount the drives or else I would have to shut it down/restart by brute force. Sometimes when a shutdown is launched, the script manage to stop gdm, but not apache and therefore halts. 

I think some of the main problems is in the drivers for the network card (ndiswrapper 1.42, DWL-G120 b2), but it could also be the usb peripheral system. I also experience hardware warnings because of too high 5VSB voltage (it should be 5.0+- 1, it is 5.7).

My question are: What changes can I make? Should I tweak some options in the makefile for ndiswrapper (i.e. smp, which i don't have)? Can anything inside linux be changed so that the memory stuffing be halted? Should I just leave as it is and buy a new system (mine was built by hand)?

Sorry for my bad language and rhetorics

---

### Post by MoLE on 2007-05-12
I suspect your intuition is probably correct in this case.  Certainly the problem affecting two different operating systems is highly suspect as a hardware issue - I doubt it's a driver issue.

I'd probably start with a memtest run to try and rule out flaky memory.  A high voltage warning on your +5v rail also suggests a potential motherboard issue.

If the system is not brand-new, a partial upgrade of the faulty components would probably be quite cost-effective.

---

