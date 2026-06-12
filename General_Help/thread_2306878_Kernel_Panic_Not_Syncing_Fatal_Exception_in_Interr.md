---
title: "Kernel Panic Not Syncing Fatal Exception in Interrupt"
date: 2015-12-19
forum: General Help
---

### Post by weizilla on 2015-12-19
I'm getting "[FONT=Lucida Console]**Kernel panic - not sycing: Fatal exception in interrupt**[/FONT]" errors with both my 14.04 installation and the 14.04.3 live cd. I have all of my hard drives disconnected, nothing external plugged in and it passed the Mem86+ test. What else should I look at?

Background:
I have a headless 24/7 file and media server which froze one day. I hard restarted it and it came back normally but froze again after 10 mins of normal operations. I determined that maybe the CPU was overheating because the fan was barely running over 800 rpm so I installed a new heatsink and fan. 

However, after installation, the computer would halt on boot with the kernel panic error. I tried all of the older kernels but they all do the same thing.

Thinking something was wrong with the system or HD, I disconnected everything and booted off a live cd of 14.04.3. At first, it would halt on boot with a "[FONT=Lucida Console]8254 timer not connected to io-apic[/FONT]" error but that was resolved with boot options of "[FONT=Lucida Console]noapic acpi=off[/FONT]". However, I still end up with the same kernel panic error.

I ran Mem86+ from the live cd and no errors were detected.

What else could be wrong?

CPU: AMD 64 3800+ Athlon X2
Heatsink: Rosewill RCX-Z1
Memory: 2 x 1GB G.Skill F1-3200PHU2-2GBNS, 2 x 512 MB Corsair Value Select VS 512MB400
Mobo: Asus A8N-SLI Premium nForce4 SLI
Video: Sapphire Radeon HD 5450
CD Rom: BenQ DW1640 16X Dual Layer DVD±RW 
Power: CS 650 M

---

