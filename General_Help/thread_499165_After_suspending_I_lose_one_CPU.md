---
title: "After suspending I lose one CPU"
date: 2007-07-12
forum: General Help
---

### Post by erlguta on 2007-07-12
I use Feisty x86 (kernel:2.6.20-16-generic)  in AMDTurion64 2xCPU
after suspending i can see in Powermanager that i lost one cpu (the policy is OK, but the second CPU does not start)
	
tests that i have made

Before suspending:

$  cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 800 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 800 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).

 and

:~#  cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
powersave ondemand conservative userspace performance
:~# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors
powersave ondemand conservative userspace performance

Everything Ok

After suspending:
 :~# cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 800 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

and

:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
powersave ondemand conservative userspace performance
:~# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors
cat: /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors: The file or directory does not exist

What happens? Why the second processor dos not start?
thanks for your help (nad time) and excuses my bad english language (I did not have any answer in the Spanish forum)****

---

### Post by erlguta on 2007-07-13
And can anybody, who haves 2 processors, try if it happens to him the same?
...after suspend look at the powermanager CPU Frequency and see if you have the 2 processors working...it will be helpful for me.
Maybe it is a bug.
Thanks in advance.

---

### Post by enigma83 on 2007-09-19
Gravedigging maybe, but I have exactly the same issue after suspending I think.  First CPU operates fine, second one apparently has no cpufreq driver.
However, the 2nd CPU is not "lost".  It still operates, still recieves jobs and runs them etc.  I can 'echo 0 > /sys/devices/system/cpu/cpu1/online' and take the 2nd CPU offline, which definately stops the 2nd CPU.  And then echo 1 to bring it back up.  But there is no cpufreq driver still.

---

### Post by asdf@gentoo on 2008-02-29
Hi guis , I'm running on gentoo , but I have same problem , I solved this by compiling the acpi_cpufreq as module ,and after resume rmmod -f (you need to have kernel with compiled force module unloading option ) and modprobe acpi_cpufreq  - now both cores are scalable and under control

---

