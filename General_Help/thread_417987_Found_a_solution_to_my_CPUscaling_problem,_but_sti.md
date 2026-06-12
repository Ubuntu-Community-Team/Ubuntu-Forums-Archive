---
title: "Found a solution to my CPUscaling problem, but still having and issue."
date: 2007-04-22
forum: General Help
---

### Post by Backdraft on 2007-04-22
My CPU scaling would not go change from anything except 50%, or 798MHz.  I found a site that recommended running this ```
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
``` from a terminal prompt as root. Not sudo, but actual root. I used sudo -i and got the root terminal prompt, ran the above code and my computer starts doing dynamic switching. All is good. 

However, everytime I reboot the machine will only work at 50% again.  I again have to open up terminal and run that code for it to start working again.  How can I get my CPUfrequtils to actually do dynamic switching each time I reboot without having to run this each time?

---

### Post by mhansen on 2007-04-22
You can always put stuff like that in /etc/rc.local.  That script is run as root during boot-up.  So put something like /bin/cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq


That should hook ya up.


Regards,
Mike

---

