---
title: "Got a Wolfdale e8400 but system info indicates 2000 MHz"
date: 2008-06-12
forum: General Help
---

### Post by heatblazer on 2008-06-12
I got a new CPU - wolfdale e8400 and additional 4 GB ram. When I open system info, it still shows me the freq. of my old e4400. Can you give some info how to actualize it?:)

---

### Post by sdennie on 2008-06-12
Are you sure this isn't related to CPU frequency scaling?  Try:

```

cpufreq-info

```

(You may have to install that first but, it will give instructions if you don't have it).

---

### Post by heatblazer on 2008-06-12
CPUs which need to switch frequency at the same time: 0
  hardware limits: 2.00 GHz - 3.00 GHz
  available frequency steps: 3.00 GHz, 2.00 GHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 2.00 GHz and 3.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 2.00 GHz - 3.00 GHz
  available frequency steps: 3.00 GHz, 2.00 GHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 2.00 GHz and 3.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.


That`s the reply from the program. Any info?

---

### Post by sdennie on 2008-06-12
That looks perfectly normal to me.  It says the max CPU frequency is 3Ghz but that it's sitting at 2Ghz to save power because it's basically idle.  The moment you do anything interesting, the CPU will immediately jump up to 3Ghz.  To see this in action, right click on the gnome panel and select Add to Panel and then add a CPU Frequency Scaling monitor.

---

### Post by heatblazer on 2008-06-12
Great, man! Thanx a lot! I`m just not used to the hardware infos :) Thank you!

---

### Post by IanW on 2008-06-12
Alternatively, check the FSB & Multiplier settings in your PC's BIOS screen.

---

### Post by Titan8990 on 2008-06-12
Just a note, Intel's version of the slow the CPU down to save energy is know as "speedstep". Many BIOS have an option to disable this feature. I only recommend disabling it if you overclock your system.

---

