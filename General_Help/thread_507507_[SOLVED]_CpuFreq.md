---
title: "[SOLVED] CpuFreq"
date: 2007-07-23
forum: General Help
---

### Post by iamstretchypanda on 2007-07-23
Problem: Cpu-freq will not change from 1000 MHz

Doing a cpufreq-info reveals:

analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  [B]current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.[/B]
  current CPU frequency is 1000 MHz.

I believe the error is the bolded section.

I've been trying to change the maximum to 2.2 GHz but i've had no luck using:
sudo cpufreq-set -g ondemand -d 1000 -u 2200 -c 0

Any help appreciated

Thanks :]

---

### Post by kevinlyfellow on 2007-07-23
I'm not familiar with cpufreq-set, but have you tried cpufreq-selector (if they aren't the same program... I don't think they are, since you have options I'm also not familiar with)?

```
sudo cpufreq-selector -c 0 -g ondemand
```

This is useful if you want to not require root permission and/or use the cpu monitoring apps to control the freq.
```
sudo chmod +s /usr/bin/cpufreq-selector
```

---

### Post by iamstretchypanda on 2007-07-23
current policy: frequency should be within 1000 MHz and 1000 MHz.
The governor "ondemand" may decide which speed to use
within this range.

As you can see, the ondemand govenor is already selected, the problem is the range the is 1000MHz minimum to 1000 MHz maximum.  I need to change the maximum to 2200 MHz.  I thought this was done with the option -u 2200.  Doing cpufreq-set -h shows the help page:

Options:
  -c CPU, --cpu CPU        number of CPU where cpufreq settings shall be modified
  -d FREQ, --min FREQ      new minimum CPU frequency the governor may select
  -u FREQ, --max FREQ      new maximum CPU frequency the governor may select
  -g GOV, --governor GOV   new cpufreq governor
  -f FREQ, --freq FREQ     specific frequency to be set. Requires userspace
                           governor to be available and loaded
  -h, --help           Prints out this screen

Notes:
1. Omitting the -c or --cpu argument is equivalent to setting it to zero
2. The -f FREQ, --freq FREQ parameter cannot be combined with any other parameter
   except the -c CPU, --cpu CPU parameter
3. FREQuencies can be passed in Hz, kHz (default), MHz, GHz, or THz
   by postfixing the value with the wanted unit name, without any space
   (FREQuency in kHz =^ Hz * 0.001 =^ MHz * 1000 =^ GHz * 1000000).

I just cant figure out how to raise the maximum, i'm puzzled.

---

### Post by iamstretchypanda on 2007-07-23
cpufreq-set, cpufreq-info, and cpufreq-selector all come in the package cpufrequtils

---

### Post by kevinlyfellow on 2007-07-23
I think I found the error :-)

I think your clockspeed you put in wasn't 2.2 GHz, instead it may have been 2.2 MHz

Try this
```
sudo cpufreq-set -g ondemand -d 1000000 -u 2200000 -c 0
```

Edit: and just to mention, cpufreq-selector is in ubuntu by default, although it may also be in the package you mentioned earlier

---

### Post by iamstretchypanda on 2007-07-23
haha... that was a VERY silly mistake.  Thanks for the help.  [solved]

---

