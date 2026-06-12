---
title: "Dual core - Don't know enough about this?"
date: 2007-02-23
forum: General Help
---

### Post by RudolfMDLT on 2007-02-23
Hi there!

I recently upgraded to a dual core system - I have read on the forums that I need the SMP kernel installed? I did this(686 - SMP) but when I try to load this kernel from the boot menu I get all kinds of errors relating 64-bit. The errors appear directly after I select the option and press enter. After this the system just sits there.

Any help would really be appreciated!

Thanks,

Rudolf

---

### Post by newlinux on 2007-02-23
The generic kernel that comes with Edgy is SMP enabled. I recommend you use that one. You can verify it by looking at gnome-system-monitor (resources panel).

---

### Post by newlinux on 2007-02-23
What I mean is you can verify it sees both cores (it will show two CPUs in gnome-system-monitor)

---

### Post by RudolfMDLT on 2007-02-23
I'm running Kubuntu? 

Anyway - I did check this and it only shows 1 CPU... but your info on the default support made me wonder so I dug a little deeper.

KSysGaurd does list two CPU's - but when I load the Clock frequency monitor I get a frequency of 2400hz, not 3400hz(which is what is actually in the machine)?

Whats up with that! 

Anyway, thanks newlinux for setting my paranoia at rest! :)

Thanks,

Rudolf

---

### Post by newlinux on 2007-02-23
Ahh I should have noted you are on Kubuntu. You could also do 
```
uname -a 
``` and if it showed SMP somewhere in the output you are good to go (for future reference).
 My mobo and processor support clock frequency scaling, so it doesn't ramp up the clock speed unless necessary. Yours may as well. In this case, if you wan't to see 3400Ghz run something processor intensive. If you don't see it go up then maybe something else is going on...

---

### Post by newlinux on 2007-02-23
I should also note that you should be able to check what frequencies are supported by doing:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

At least, that's where that information is on my system

---

### Post by RudolfMDLT on 2007-02-24
the output reports:

3400000 2400000 


So thats good right? Thanks again!

---

### Post by newlinux on 2007-02-24
> **RudolfMDLT said:**
> the output reports:

3400000 2400000 


So thats good right? Thanks again!

Yep, everything is as it should be then. Happy ubuntuing.

---

