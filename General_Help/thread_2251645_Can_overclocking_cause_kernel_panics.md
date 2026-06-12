---
title: "Can overclocking cause kernel panics?"
date: 2014-11-05
forum: General Help
---

### Post by jdallara on 2014-11-05
Hello,

  I've been working on overclocking my system and it works fine to a certain point past which I start getting kernel panics.  The details:
M/B: Asus Z97M-PLUS
CPU: Intel i5-4670K
MEM: Corsair Vengeance 2400MHz
O/S: Ubuntu 14.10

I installed the OS with the system running at its normal out-of-the-box 3.4GHz.  I can increase the core multiplier up to 41, 4.1GHz, with no problem.  Core temperatures are below 140F and the core voltage is 1.164v so I don't think temperature or voltage is an issue.  As soon as I increase the multiplier to 42, 4.2GHz, I start getting kernel panics (Caps lock and Scroll lock keyboard lights flashing) and the system reboots.  Sometimes this occurs within a minute or two of each other.  Syslog doesn't seem to have anything of interest noted.  Temperatures are still below 145F and the voltage is only 1.183v.  Is there something in the kernel that is getting off balance when I increase the speed to this point?  Do I need to reinstall the OS with the multiplier at 41 and start from that point?  Any insight would be appreciated.

Thank you,
Jon.

---

### Post by tgalati4 on 2014-11-06
You would need to do some research on your specific motherboard.  Some are better than others for overclocking.  Then you would have to research your specific i5 processor--you might need to pry it off to get the production code and then research that.  CPU's are often tested and "binned", put in bins for stability at different speeds.

42X represents a 23.5% overclock which is agressive.  Most safe overclocks are 10 to 15%.  It's possible that the power circuitry can't provide enough current for the CPU, or the clock has noise at 4.2 GHz--we are talking about microwave frequencies.  If the board doesn't have enough shielding for those higher frequencies, then noise can trip up the clock, which will trip up the CPU.  You would need an expensive oscilloscope to check the clock pulses at that speed.  There could also be issues with the I/O chips handing memory at higher speeds.  There are several places where overclocking can fail.

Spend some time on the overclocker's forums and you will get a feel what's involved for extreme overclocking.  Usually testing will reveal limits, regardless of what is on paper.  In your case, you are limited to 4.1 GHz.

---

