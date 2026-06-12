---
title: "[SOLVED] Advanced CPU speed control"
date: 2008-06-13
forum: General Help
---

### Post by squaregoldfish on 2008-06-13
Hi there,

Having just discovered cpufreq and friends, I've been wondering how much it's possible to fine-tune the settings for different speeds.

In my particular case, I want to strike a balance between running BOINC projects and saving a bit of power at the same time, so I'd like to set up my CPU something like this:


No tasks running => 1.0 GHz (lowest speed)
Only low priority (nice) tasks running => 2.0 GHz
Normal tasks running => 2.4 GHz (full speed)

I reckon I can save around 10% of my machine's power consumption this way, while still doing some useful work (albeit slightly more slowly).

Is this feasible? I suppose there's two possible options - the first and easiest would be if the cpufreq utilities can do this. The second would be if a script could analyse the priorities of active processes, and 'manually' change the CPU speed accordingly.

Anyone have any thoughts on this?
Steve.

---

### Post by squaregoldfish on 2008-06-18
OK, so after a bit of digging around, I managed to get what I needed by tweaking various bits and pieces in /sys/devices/system/cpu/cpu0/cpufreq

Running the ondemand governor, I made it ignore the nice processes (i.e. BOINC) as follows:

```
echo 1 > ondemand/ignore_nice_load
```

My CPU has the ability to run at 2.4GHz, 2.2GHz, 2.0GHz, 1.8GHz or 1.0GHz. I decided I didn't want to lose too much performance in the BOINC processing, so I prevented the CPU scaling right down to 1.0GHz, instead setting the lower limit to 1.8GHz:

```
echo 1800000 > scaling_min_freq
```

And that's my system set up. When I'm using the machine, the CPU steps up to full speed as required. When I'm not using it, the CPU scales back to 1.8GHz and continues to run BOINC at that speed.

I don't yet know whether these values will persist across a reboot, or whether I'll need to write a script to set them up again. That won't be hard though.

**EDIT**: The changes don't survive a reboot, so I added the necessary lines to /etc/rc.local

Steve.

---

