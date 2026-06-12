---
title: "Ubunutu not finding correct CPU?"
date: 2007-02-09
forum: General Help
---

### Post by sxturbo on 2007-02-09
I am running Ubuntu 6.10 with an Athlong 64 3700+.  

Under device manager it shows 'unknown' for my CPU. But with a 'desktlet' I installed it shows the correct cpu, but running only at 1000mhz. 

Is there something I need to install in the x86 version for it to detect my AMD 64 chip correctly?

[IMG]http://www.mitchweber.info/images/cpu.jpg[/IMG]

---

### Post by vigleik on 2007-02-09
"less /proc/cpuinfo" will tell you what the kernel thinks your processor is, together with the clockspeed etc. If the information there is correct you have nothing to worry about. It is possible that your processor runs at 1GHz when idle and 2GHz when busy, that's what mine does. Fire up a CPU-intensive program and check /proc/cpuinfo again.

---

### Post by sxturbo on 2007-02-09
K, just tried that and it does show up with 1000mhz nomatter what.

any ideas?

---

### Post by fenian on 2007-02-10
What does it say in the post screen before it boots ito ubuntu?Is the BIOS reading the chip correctly?Power issues (surges,bad psu)and memory issues can cause the BIOS to underclock the CPU.

---

### Post by warkro on 2007-02-10
i'm experiencing the same thing, I have an AMD athlon 2.2Ghz and it only reads 800Mhz when I'm idle...However when I have 4-6 programs running it goes up. Add Cpu scaling applet to your panels and you'll see. Don't worry about it.

---

### Post by vigleik on 2007-02-10
> **sxturbo said:**
> K, just tried that and it does show up with 1000mhz nomatter what.

any ideas?

Please post output of "less /proc/cpuinfo" when you're **sure** the CPU is maxed out. For example, do some audio or video encoding (or both at the same time).

If you still can't get more than 1GHz you probably have a hardware problem, and as fenian suggested you should check your bios. (I guess it's possible, though highly unlikely, that you've discovered a bug in the linux kernel which makes powersave always be on.)

---

