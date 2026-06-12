---
title: "CPU Frequency Scaling not working properly"
date: 2006-11-20
forum: General Help
---

### Post by garymansell on 2006-11-20
Hi,

I have successfully installed Ubuntu Edgy onto my HP Pavilion ZD8044 Laptop. The laptop has a 3.2Ghz P4 Processor.

I noticed, though, that the CPU Frequency Scaling was not working. When I added the CPU Frequency Monitor onto the panel, it said that the CPU Frequency scaling was not working.

On further investigation, it appears that the p4_clockmod module was not getting installed into the kernel at boot time and that I need this to be installed for the frequency scaling to work.

When I manually insert the module with the command sudo modprobe p4_clockmod I can then control the CPU Frequency scaling by echo'ing one of several control modes to the pseudo file /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

It seems to me that everytime the p4_clockmod module is inserted, it defaults to the performance setting for the scaling_governor. It seems to me that a more appropriate setting would perhaps be conservative.

I also notice that when the power is removed from the laptop and it is running on batteries, that the cpu frequency is not reduced.

Please can someone advise me how to configure my laptop so that the p4_clockmod module is inserted into the running kernel at boot.

Please can someone also advise me how to configure my laptop so that when the machine is idle and on power, the cpu speed is reduced and also so that when the laptop is on battery power, the cpu frequency is reduced.

Thanks in advance

Gary

---

