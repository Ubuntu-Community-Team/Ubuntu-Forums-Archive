---
title: "Another guy with a fan speed/noise problem"
date: 2012-11-25
forum: General Help
---

### Post by bernardosgr on 2012-11-25
OK, first of all, this is not a duplicate, I've read and tried every single thing suggested for solving this sort of problem in this forum and all over the internet and nothing worked, everything from changing grub configurations to installing jupiter and other fan controller software, cpufreqd and cpufrequtils, every single thing... The computer still keeps making to much noise, which doesn't happen when I run windows 7....

I'm running a dual-boot system with Ubuntu 12.10 (quantal) 32bit and Windows 7, Kernel Linux 3.5.0-18-generic GNOME 3.6.0

I have 2 GB RAM and an Intel® Core™2 Duo CPU E4500 @ 2.20GHz × 2

my graphics card is NVidia GeForce 9600 GT

PLEASE!!! HELP ME!!! Because I am in serious need of doing some work and it's becoming unbearable to work in such noisy conditions

Thank you very much

---

### Post by Mark Phelps on 2012-11-25
You need to look at this in the PROPER context!  IS is NOT a "fan speed/noise" problem; instead, it is a "processor overheating" problem.  

The fans are designed to operate at whatever speed is needed to prevent the processor from overheating.  The ONLY solution in this case is to throttle back the processor -- which is what the Jupiter app tries to do.  

IF you forcibly slow down the fans, you risk either burning out the processor, or (if autotemp shutdown is enabled) having your PC suddenly shut down on you when it gets too hot (due to the fan speed being reduced).

---

### Post by bernardosgr on 2012-11-25
But isn't that strange? The CPU usage can't be that high for it to overheat and force the fans to run at such speed... As I said I run windows normally with no problems, there certaily must be something wrong... Whether I'm running 7 apps or none, the fans are at the same speed, shouldn't they adjust according to the CPU's charge??

---

### Post by personalpc on 2012-11-25
Try re-applying thermal compound and make sure your bios allows fan control. You could always install a fan controller just make sure you have good compound like arctic silver. If its a laptop some use proprietary drivers such as the toshiba which has the updates in the repos

---

### Post by bernardosgr on 2012-11-27
The problem has been fixed by someone in a different site: askubuntu.com/questions/221794/once-again-the-fan-speed-noise-problem-on-desktop

It seems I didn't have the appropriate driver installed. I installed it, rebooted and done!

---

