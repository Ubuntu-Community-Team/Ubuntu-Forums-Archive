---
title: "System sluggish"
date: 2008-02-14
forum: General Help
---

### Post by BobLand on 2008-02-14
I have a new Intel dual-core 4400 @2 GHz, 2Gb RAM, 2048K cache, NVidia 8400GS, latest driver installed, 250G HD.

I've been using the machine for about a month and it's been pleasurably fast.  Yesterday, I transfered about 40k files from an old archived Windows disk onto my Ubuntu box.  After that, the machine acts like it wants to go away to a rest home.

During this period, I installed and ran sauerbraten.  Worked fast and consistently except for an occasional lockup.  However, it now randomly stops and starts so it is useless.  I just downloaded a new version and have the same results.

When I open Firefox or Swifteasel, both take a much longer time to open and don't have that same snap.  Outside of sauerbraten, there is no definitive benchmark I can offer.  The system just seems too slow for its capabilities.

Are there caches that need or can be flushed?  I looked at /proc/cpuinfo and everything looks normal as far as I can tell.

Any suggestions are greatly welcomed!
Thanks,
bobland

---

### Post by tcpip4lyfe on 2008-02-14
What do your logs tell you in /var/log?  Anything useful?

---

### Post by BobLand on 2008-02-14
Checked the logs but nothing unusual or error(s).  One thing - is it possible to overwhelm the swap and if that's possible can it be flushed?

---

