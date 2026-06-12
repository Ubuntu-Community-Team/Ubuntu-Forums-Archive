---
title: "Strange RAM limit"
date: 2008-01-24
forum: General Help
---

### Post by amorangi on 2008-01-24
I've just put another 2GB in my machine to take it up to 4GB, and before I begin yes I know 32bit Ubuntu won't see it all. However System Monitor reports only 3GB exactly, and Top says 3107584k which is slightly under 3GB. I would have thought with 4GB the system should report around 3.2GB available. Does anyone know why I might be seeing less? 
The memtest+ at bootup scans 4096MB fine, and the BIOS happily reports 4096MB available as well.

I'm download 64bit now, but I'm a little perplexed by "missing" more RAM than I expected.

---

### Post by PeterJS on 2008-01-24
Are you using shared vRAM? that counts toward the 3.2GB limit but wouldn't show up there.

---

### Post by amorangi on 2008-01-24
No, using 8800GTS video, Q6600 CPU, 975 motherboard

---

### Post by fumbles on 2008-01-24
Thats normal... You video card ram counts towards the limit. When using XP 32bit I only see 3GB too. Why not just use a 64bit version of Ubuntu?

---

### Post by PeterJS on 2008-01-24
Even if it's dedicated memory? Hmm learn something new everyday around here, I thought that was just an issue with shared memory.

---

### Post by pointone on 2008-01-24
A 32 bit OS can only access 4 GB worth of addresses; this includes system RAM, video RAM, the BIOS, and other devices in your system.

---

### Post by amorangi on 2008-01-24
Thanks fumbles, that explains it - 320MB is on my video card which is exactly the discrepancy. 
As I said, I am already downloading the 64bit version and will reinstall as soon as that has finished. I just didn't realise that the memory limit included video card RAM.

---

### Post by dabl on 2008-01-25
Sounds like your setup is very similar if not identical to mine.  4G of RAM and an 8800GTS 320 video card, on an Intel D795XBX2..

With 64-bit KInfoCenter shows Total physical memory: 4,150,722,560 bytes = 3.87GB.

:)

---

### Post by amorangi on 2008-01-25
I've now switched to 64 bit and noticed it's definitely faster, even when not using over 2GB RAM. VMs especially are now much quicker. Perhaps my hardware is better able to take advantage of 64bit, since I've heard a lot of people complain there's little difference, and I've heard a lot of FUD, but now I wish I'd made the switch sooner. 
Top now reports 4051220k total, which is near enough to 4GB for me.

---

### Post by fyo on 2008-01-25
> **amorangi said:**
> I've now switched to 64 bit and noticed it's definitely faster, even when not using over 2GB RAM. VMs especially are now much quicker. Perhaps my hardware is better able to take advantage of 64bit, since I've heard a lot of people complain there's little difference, and I've heard a lot of FUD, but now I wish I'd made the switch sooner.

64bit Ubuntu is FASTER. Significantly so. It's great to see that posted sometimes ;-)

I have no idea why some people perpetuate the myth that there's little difference.

Even if you disregard all the memory issues that are solved on 64bit, you still get a typical performance increase of 15-30%, with some apps running 70%, 100% (or even more) faster. A *very* few apps are a few percentage points slower. Search around for independent testing - preferably for the apps that matter to YOU.

Note that LAME encoding is one of the few apps that don't see any appreciable increase, at least in the comparisons I've seen (which are admittedly getting a bit long in the tooth).

---

