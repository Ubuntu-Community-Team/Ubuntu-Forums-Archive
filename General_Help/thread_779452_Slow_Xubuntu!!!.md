---
title: "Slow Xubuntu???!!!"
date: 2008-05-02
forum: General Help
---

### Post by Kyle54 on 2008-05-02
256MB RAM, 800MHz Crusoe Processor (equivalent to about 700Mhz P3), 30GB Hard Drive.

70-80% CPU when idle. 95-100% when simply loading the System Monitor. Why? It's VERY sluggish, the system has to catch up with the mouse simply to light up certain icons when I go over them. Fresh install.

Why is it slow?

Latest stable hardy release, too.
I've had Xubuntu run on SLOWER machines and it ran great! Why is it so bad with my Fujitsu laptop (with the above specs)?

Would reinstalling with Dapper solve this problem? (maybe some incompatibility with Crusoe or something?)

It's dual booted with XP SP3, and XP is WAY faster than Xubuntu is. (XP isn't exactly a speed demon when you're running on 256MB of RAM and an 800MHz processor, but it runs a hell of a lot better than Hardy Xubuntu.) why?

---

### Post by ajmorris on 2008-05-03
hi there,
when you experience this sluggishness, could you please post the output of the command top.

AJ

---

### Post by mac9416 on 2008-05-03
I have installed XUbuntu on a computer that should have been running DOS but it was too slow. I installed Ubuntu (normal) and that was much faster. Not right but true. Sorry.
Good luck making it faster or installing Ubuntu, whichever you choose.

---

### Post by Kyle54 on 2008-06-24
> **ajmorris said:**
> hi there,
when you experience this sluggishness, could you please post the output of the command top.

AJ
**THIS IS WHEN IDLE**

top - 19:23:32 up  2:43,  2 users,  load average: 1.08, 0.69, 0.58
tasks: 83 total, 2 running, 81 sleeping, 0 stopped, 0 zombie
CPU(s): 10.2%us, 6.6%sy,0.0%ni,83.2%id,0.0%wa,0.0%hi,0.0%si,0.0%st
Mem: 239348k total, 168188k used, 70236k free, 10756k buffer
Swap: 1253028k total, 64560k used, 1188468k free, 63272k cached

Xorg is always the highest on the list of apps. under VIRT it says 33260, under RES it says 14m, under SHR it says 4992, and it says S (not R), and when idle, takes up 8% CPU, and 7.8% MEM.

below it is always top, and below that is always xfce4-terminal.
-----------------
could there be a swap problem? remember i have a 30gb hard drive

---

### Post by Kyle54 on 2008-06-25
you guys are a huge help.

---

### Post by rubicon on 2008-06-25
Please attach output of command 'ps aux'. Right here wholly, just surround it with [code] tags so it will be scrollable.

---

### Post by mikjp on 2008-06-25
> **Kyle54 said:**
> Xorg is always the highest on the list of apps. under VIRT it says 33260, under RES it says 14m, under SHR it says 4992, and it says S (not R), and when idle, takes up 8% CPU, and 7.8% MEM.

Do you have correct video driver? 

Try to turn all desktop effects of, they might use processor a lot.

---

### Post by candlerb on 2009-05-28
> **Kyle54 said:**
> 256MB RAM, 800MHz Crusoe Processor (equivalent to about 700Mhz P3), 30GB Hard Drive.

70-80% CPU when idle. 95-100% when simply loading the System Monitor. Why? It's VERY sluggish, the system has to catch up with the mouse simply to light up certain icons when I go over them. Fresh install.

Why is it slow?


Two thoughts: maybe you have some sort of spurious interrupts going on, or maybe you are swapping to disk excessively.

Post the outputs of:

    cat /proc/interrupts

    free

Also, run "vmstat 2" for a few seconds, and post the output of that while you're doing some stuff like moving the mouse around.

If it's interrupts: it may be possible to turn off the offending hardware in the BIOS. If it's swapping: you could try upping the RAM to 512MB, or using Xubuntu.

---

