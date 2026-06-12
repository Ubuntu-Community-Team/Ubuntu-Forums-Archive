---
title: "CPU frequency scaling not working at all"
date: 2007-08-08
forum: General Help
---

### Post by buttari on 2007-08-08
Hi all,
my cpu frequency scaling doesn't work at all and the proc runs constantly at 50% of its clock speed.
So available frequencies are:
```

[~]$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2000000 1667000 1333000 1000000

```

and available governors are:
```

[~]$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
userspace powersave conservative ondemand performance

```

I tried all the possible frequencies and governors but /proc/cpuinfo always reports 1000 MHz. To change frequency/governor I tried cpufreq-selector like this
```

[~]$ sudo cpufreq-selector -c 0 -f 2000000

```

or

```

[~]$ sudo cpufreq-selector -c 0 -g performance

```

but doesn't work.
Anybody can help?

Thanks

Alfredo

---

### Post by hikaricore on 2007-08-08
Have you set your governor to performance?

Check the output of:

```
cpufreq-info
```

---

### Post by buttari on 2007-08-08
> **hikaricore said:**
> Have you set your governor to performance?

Check the output of:

```
cpufreq-info
```

```

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, conservative, ondemand, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, conservative, ondemand, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.

```

even if I do
```

sudo cpufreq-set -f 200000

```

nothing changes. I installed the frequency monitor applet and I noticed that for few seconds after I login, the frequency of the cores goes up to 2 GHz but then it drops to 1 GHz and sits there for ever.

Thanks

Alfredo

---

### Post by yorkie on 2007-08-08
Open a few apps your cpu speed display will increase its as it says ondemand  it will only run at a speed you need to run apps

---

### Post by yorkie on 2007-08-08
some info you might find helpful

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by yorkie on 2007-08-08
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

correction to previous message

---

### Post by buttari on 2007-08-08
> **yorkie said:**
> Open a few apps your cpu speed display will increase its as it says ondemand  it will only run at a speed you need to run apps

What is the response time for changing the frequency? I mean, if I issue the command to change the frequency, how long does it take before the change takes effect? Also, is there anything that prevents changing the frequency when the cpu temperature is too high? 
For no particular reason, it started working now.

Thanks

Alfredo

---

### Post by Mr. Swiveller on 2007-08-08
I have the same problem. There is a thread on this bug here: [https://bugs.launchpad.net/ubuntu/+s....20/+bug/88899](https://bugs.launchpad.net/ubuntu/+s....20/+bug/88899).

So far, I have not heard of a permanent solution. Right now, my CPU works at 1.8 Ghz, but this is a rarity - it nearly always stays at 800 Mhz. 

Could this indeed be some sort of temperature safeguard? Last time I tried to force my CPU to work at 1.8 Ghz I noticed CPU temperature was close to 90 degrees celcius.

Swiveller

---

### Post by buttari on 2007-08-08
> **Mr. Swiveller said:**
> I have the same problem. There is a thread on this bug here: [https://bugs.launchpad.net/ubuntu/+s....20/+bug/88899](https://bugs.launchpad.net/ubuntu/+s....20/+bug/88899).

So far, I have not heard of a permanent solution. Right now, my CPU works at 1.8 Ghz, but this is a rarity - it nearly always stays at 800 Mhz. 

Could this indeed be some sort of temperature safeguard? Last time I tried to force my CPU to work at 1.8 Ghz I noticed CPU temperature was close to 90 degrees celcius.

Swiveller

Mr. Swiveller,
what proc do you have? I have a CoreDuo and it constantly runs between 80 and 90 degrees even for light loads (like browsing) .
thanks

Alfredo

---

### Post by Mr. Swiveller on 2007-08-08
Hi Alfredo -

My CPU is an AMD Turion 64-bit 'Mobile Technology ML-34'. Right now the temperature is about 90 celcius even though only Amarok, Firefox, and  Firestarter are running.

Frequency has just now switched to 800 Mhz, btw. Seems like it might well have to do with system temperature.

Cheers,

Swiveller

---

### Post by EXCiD3 on 2007-08-08
Are you sure it is always running at 50% or so? My Core 2 Duo runs at 1 GHz most of the time, but switches to 1.83 GHz when i do something important and switches back quickly. It jumps around a lot of the time.

---

### Post by Mr. Swiveller on 2007-08-09
Yes - quite sure. A post I found (forgot which one, unfortunately) suggested that the system does, indeed, force down the CPU frequency if the system gets too hot. A good feature, but, as I found out, acpi -t reads system temperature incorrectly. I installed LM-sensors, and it gives me temperatures far below the output from an 'acpi -t' command.

acpi -t: 

Battery 1: charged, 98%
     Thermal 1: passive , 84.0 degrees C
     Thermal 2: passive , 72.0 degrees C
     Thermal 3: passive , 95.0 degrees C

sensors:

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +32°C

I think that this is the problem Alfredo & I have encountered - outrageous temperature readings from the ACPI module.

Cheers,

Swiveller

EDIT

Take a look at this thread: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/22336](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/22336).

It's happening to lots of people.

---

### Post by hikaricore on 2007-08-09
Did you ever attempt to set the governor to **perfomance** like I suggested?

In your response I only saw you tried changing the clock speed and not the governor.

---

### Post by buttari on 2007-08-09
> **hikaricore said:**
> Did you ever attempt to set the governor to **perfomance** like I suggested?

In your response I only saw you tried changing the clock speed and not the governor.

yes, I did. Here what's happening now:
CPU 0 is using "ondemand" and the frequency varies from 1 GHz up to 2 GHz depending on the load

CPU 1 is using  "performance" but it's stuck at 1 GHz and there's no way I can change the governor nor the frequency.

Alfredo

---

### Post by buttari on 2007-08-09
Hi all,
I'm starting to suspect that the problem is coming from suspending the laptop. I just rebooted it, in fact, and it's working fine now (i.e. both CPUs on "ondemand" with frequency changing depending on the load).
Also, before rebooting, even if CPU 1 was fix at 1 GHz, its temperature was always way higher than CPU 0 (say 89 versus 80 degrees). Now both CPUs are around 80 degrees.

Does anybody have an idea of what's happening here?

Thanks

alfredo

---

### Post by Mr. Swiveller on 2007-08-10
I have found ACPI support is still somewhat patchy in Linux - if you search the forums, you will find many people are having problems related to suspend / hibernate / stand-by modes.

The temperature-readouts you are getting are very high, though. Have you tried installing lm-sensors, and probing your system temperatures in that way? I am quite certain that the problems on my own setup are caused by faulty ACPI temperature readings - sometimes the temperatures ACPI-V reports are 40 degrees Celcius higher than those from lm-sensors!

Cheers,

Swiveller

---

### Post by buttari on 2007-08-10
> **Mr. Swiveller said:**
> I have found ACPI support is still somewhat patchy in Linux - if you search the forums, you will find many people are having problems related to suspend / hibernate / stand-by modes.

The temperature-readouts you are getting are very high, though. Have you tried installing lm-sensors, and probing your system temperatures in that way? I am quite certain that the problems on my own setup are caused by faulty ACPI temperature readings - sometimes the temperatures ACPI-V reports are 40 degrees Celcius higher than those from lm-sensors!

Cheers,

Swiveller

Swiveller,
the question is, how do you know that lm-sensor is right and "acpi -V" is not? I would say "acpi -V" is right in my case since I can really get burnt touching the exhaust pipe of my laptop.

Anyway, I am 99% sure that the problem with the frequency scaling comes from suspending the laptop. I'm filing a bug report in launchpad.

Thanks

Alfredo

---

### Post by ukripper on 2007-08-10
Try :

```
sudo cpufreq-set -g performance
```

---

### Post by buttari on 2007-08-10
> **ukripper said:**
> Try :

```
sudo cpufreq-set -g performance
```

Yes,
I tried it already. All the possible ways to change the frequency or the governor have been tried. When resuming from suspend they have no effect on one of the CPUs.

Thanks

alfredo

---

### Post by Mr. Swiveller on 2007-08-10
> **buttari said:**
> Swiveller,
the question is, how do you know that lm-sensor is right and "acpi -V" is not? 

Haha, you're right there :-)! 

The reason why, in my case, I trust lm-sensor more is that the computer's case and exhausts are mostly cool. I also find it somewhat unlikely that my CPU would, at times, approach 100 degrees Celcius , even though it is running at less than half its maximum frequency and all I'm using is OpenOffice, Amarok, and Firefox.

In any case, I hope your problem will be solved soon.


Cheers,

Swiveller

EDIT

If anyone is still reading this - ACPI seems to work far better on my system now I've upgraded to Gutsy Herd 4. Lower temperature read-outs and fully functional frequency policies.

---

