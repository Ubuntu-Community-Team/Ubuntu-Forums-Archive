---
title: "Only one core recognized from an Athlon X2"
date: 2008-03-18
forum: General Help
---

### Post by Raptor354 on 2008-03-18
First off, I hope I'm not stepping on any toes by putting this thread in this category.

My problem is this:

I didn't like the fact that a guest system in VMware slows down according to your CPU clock.  When I tried to disable the CPU throttling and rebooted, it now only recognizes one core and deems the other non-responsive.

If it'll help, I'll post the results of dmesg | grep CPU:

[    0.000000] Initializing CPU#0
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.372000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[    5.352000] CPU #1 not responding - cannot use it.
[    5.392000] Brought up 1 CPUs
[    5.596000] Switched to high resolution mode on CPU 0

My questions are this:
1: What is the proper way to "disable" CPU throttling?
2: What is my problem in the first place?
3: Is there a program out there that will give me accurate CPU temp readings?  I'm fairly sure that 50 degrees F isn't correct.  (I'm using Computer Temperature Monitor 0.9.6.1)

It's kinda handy to have two cores to run VM's on, so I'd like control of my other one back. ;)

Thanks in advance.

Raptor354

---

### Post by Raptor354 on 2008-03-19
bump

---

### Post by Raptor354 on 2008-03-22
bump again...

---

### Post by Raptor354 on 2008-03-22
Might there be a way to force it to see both cores?

Raptor354

---

### Post by dcstar on 2008-03-22
> **Raptor354 said:**
> 
.........
1: What is the proper way to "disable" CPU throttling?
2: What is my problem in the first place?
3: Is there a program out there that will give me accurate CPU temp readings?  I'm fairly sure that 50 degrees F isn't correct.  (I'm using Computer Temperature Monitor 0.9.6.1)

It's kinda handy to have two cores to run VM's on, so I'd like control of my other one back. ;)


1: You use the standard tools, like the CPU Frequency Scaling applet, so reverse what you did if you want things back to normal.

2: There is no problem, the system will automatically use all the CPU resources it needs "On Demand".

3: "Brisbane" core X2 CPU temp diodes read ~20C lower than actual temp - this is a known AMD bug.

4: Running both cores in VMs under the current VMware server is fraught with problems as the host using one of the cores can cripple VM performance - just use one core in your VMs and things will suddenly appear more stable.

---

### Post by Raptor354 on 2008-03-23
1: I simply ininstalled powernowd :)

2: The problem I was having was that inside the VM when the CPU was throttled, all the apps were running at ~46% their normal speed.  Even screen refresh rates were affected.

3: Ah!

4?: Yes, I never run both cores to the same VM.  However I do run 2 VMs at once...

Thanks, 

Raptor354

---

