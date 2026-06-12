---
title: "CPU Scaling"
date: 2007-02-25
forum: General Help
---

### Post by JELO on 2007-02-25
Hello,
I've currently got an Athlon 64+ oc'd from 2.0GHz to 2.43.  I also have support for Cool and Quiet, which runs my cpu at x amount then runs it at full speed when demand is detected.  On the CPU frequency monitor in gnome it only says it's running at 2Ghz at full.
Issuing the command
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
shows my available frequencies as 2.0GHz, 1.8, 1.0.
When I turn off Cool and Quiet on my motherboard, the frequency monitor in gnome, shows up at the correct speed 2.43.
Following the guide here
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)
I am able to manually choose my frequency from the monitor now (if I enable cool and quiet)
Now my question is how can I get Ubuntu to recognize and be able choose my OC instead of just the <= default speed while being able to keep cool and quiet enabled.

---

