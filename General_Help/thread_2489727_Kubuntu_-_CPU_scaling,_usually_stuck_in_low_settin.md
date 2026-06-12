---
title: "Kubuntu - CPU scaling, usually stuck in low setting"
date: 2023-08-08
forum: General Help
---

### Post by Starcraftmazter on 2023-08-08
Hi

I have a laptop with AMD Ryzen 7 5800H, and I have Kubuntu 22.04 (work requires LTS version). This CPU can scale between 1200 Mhz - 2400 Mhz - 3600 Mhz. The problem is, 80% of the time, it's stuck at 1200Mhz which is noticeably very laggy.

I've tried to search for and use some tools to manually set the speed, but nothing has worked. I'm wondering if someone can help me - ideally I want to pick myself what the speed should be (most of the time I'd want the full speed, maybe sometimes 2.4Ghz, and probably never 1.2Ghz). Or at least a far more aggressive scaling algorithm.

Most recently I tried ```
sudo cpupower frequency-set -f 3200
``` however even though the output makes it seem like it's working, it doesn't actually do anything.

Thanks

---

### Post by MAFoElffen on 2023-08-09
If it wre me, the first thig I would do is to look at what is possible, and what is there as profiles and settings. Such as this:
```

mafoelffen@msi-ubuntu:~$ grep . /sys/devices/system/cpu/cpu0/cpufreq/*
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus:0
/sys/devices/system/cpu/cpu0/cpufreq/base_frequency:3000000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq:5500000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq:800000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_transition_latency:0
/sys/devices/system/cpu/cpu0/cpufreq/energy_performance_available_preferences:default performance balance_performance balance_power power 
/sys/devices/system/cpu/cpu0/cpufreq/energy_performance_preference:performance
/sys/devices/system/cpu/cpu0/cpufreq/related_cpus:0
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq:5511247
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq:5500000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq:800000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed:<unsupported>

```
I feel that Doug S. is the best on these kinds of things. I hope that he sees this thread and responds. He tests all the kernels, and knows of where things are in the sysfs for CPU's and what settings affect what there. I trust him and what he says. He was the person who inspired me to learn more about the sysfs.

From what I learned is that if you are running the intel_pstate driver running in one of the active modes doesn't allow you to set a particular frequency directly  because the sysfs gets that value from a read, so that file is considered as a read-only file... Doug S. could correct me if I am wrong on that, but because of that
```

sudo cpupower frequency-set -f 3200

```
...fails to do anything... But you 'can' change the maximum and minimum frequencies that the driver is allowed to set as follows:
```

sudo cpupower frequency-set -u 3200mhz
sudo cpupower frequency-set -d 3200mhz

```
that would set the min and max values. If you use
```

sudo cpupower frequency-info

```
...in the output from that, it has the possible ranges of the frequencies that can be set. At least, that is how I understand that.

...which would be equivalent to writing the value directly to the sysfs files...
```

sudo echo 320000 > /sys/devices/system/cpu/cpu[0-9]/cpufreq/scaling_min_freq
sudo echo 320000 > /sys/devices/system/cpu/cpu[0-9]/cpufreq/scaling_max_freq

```

What do you think it should be doing? I can tell you that I have my CPU freqs, load % and such, made into graphs & gauges in Conky to display on my workstation desktop while I work. It is not as active as I first thought it would be. I also display my storage pool and network loads during testing.

---

### Post by Starcraftmazter on 2023-08-09
I am not sure this is working completely - I'm guessing it's meant to set the minimum and maximum? In any case, after running both, there are still some cores running at much lower speeds (even 600Mhz).

```

sudo cpupower frequency-set -u 3200mhz
sudo cpupower frequency-set -d 3200mhz

```

```

analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency:  Cannot determine or is not supported.
  hardware limits: 1.20 GHz - 3.20 GHz
  available frequency steps:  3.20 GHz, 1.30 GHz, 1.20 GHz
  available cpufreq governors: conservative ondemand userspace powersave performance schedutil
  current policy: frequency should be within 3.20 GHz and 3.20 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency: 3.20 GHz (asserted by call to hardware)
  boost state support:
    Supported: yes
    Active: yes
    Boost States: 0
    Total States: 3
    Pstate-P0:  3200MHz
    Pstate-P1:  1300MHz
    Pstate-P2:  1200MHz
&#10140;  bin cat /proc/cpuinfo|grep 'cpu MHz'
cpu MHz         : 3200.000
cpu MHz         : 3200.000
cpu MHz         : 3200.000
cpu MHz         : 495.330
cpu MHz         : 522.241
cpu MHz         : 490.589
cpu MHz         : 3200.000
cpu MHz         : 409.653


```



To answer your question of how I expect it to work, I reckon 1.2Ghz is maybe only for singular tasks such as watching a movie, if it can be decoded by igpu, I don't think it's possible to do any sort of work on that speed, 2.4Ghz might be ok for some light web browsing, but given I use this laptop for work, I think 99% of the time I would just want the full speed. If there are no keystrokes or mouse movements, that is perhap the only time to downclock, but doing anything, it needs to go to full speed straight away IMO.

Thank you.

---

### Post by Doug S on 2023-08-10
Your system appears that it might be in some sort of throttled state, as the active CPU frequencies are so very low. The exact 3200.000 numbers are likely stale (the CPU is idle, and therefore the reported frequency is the default because there is no current value).
Could you post the output similar to what MAFoElffen listed, except for all CPUs:

```
grep . /sys/devices/system/cpu/cpu*/cpufreq/*
```

And what kernel version?

EDIT: The way to know if a listed CPU frequency is real or a stale default is that perfect round numbers of the default clock rate are stale and non-perfect numbers are real. I am saying this:

```

cpu MHz         : 3200.000  <<< Stale, meaningless
cpu MHz         : 3200.000 <<< Stale, meaningless
cpu MHz         : 3200.000 <<< Stale, meaningless
cpu MHz         : 495.330   <<< real, and throttled
cpu MHz         : 522.241   <<< real, and throttled
cpu MHz         : 490.589   <<< real, and throttled
cpu MHz         : 3200.000 <<< Stale, meaningless
cpu MHz         : 409.653   <<< real, and throttled

```

Just as a test, and in an attempt to avoid throttling, from a fresh boot I would try to keep CPU frequencies low. So set the powersave governor:

```

echo powersave | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

``` 

keep looking at your CPU frequencies as you do stuff:

```
grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
```

---

### Post by Starcraftmazter on 2023-08-14
Yep, here is a paste of that first command: [https://paste.ubuntu.com/p/J5xFnGTYnf/](https://paste.ubuntu.com/p/J5xFnGTYnf/)

I will try the powersave governor.

Seems like so far, the "real" speeds are very close to 1200mhz and sale ones at 1200mhz flat, every time I checked.

---

### Post by Doug S on 2023-08-15
From your listing with the performance governor:

```

/sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq:1130883
/sys/devices/system/cpu/cpu10/cpufreq/scaling_cur_freq:631388
/sys/devices/system/cpu/cpu11/cpufreq/scaling_cur_freq:406595
/sys/devices/system/cpu/cpu12/cpufreq/scaling_cur_freq:411844
/sys/devices/system/cpu/cpu13/cpufreq/scaling_cur_freq:507998
/sys/devices/system/cpu/cpu14/cpufreq/scaling_cur_freq:399666
/sys/devices/system/cpu/cpu15/cpufreq/scaling_cur_freq:[COLOR="#FF0000"]1892512[/COLOR]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_cur_freq:523883
/sys/devices/system/cpu/cpu2/cpufreq/scaling_cur_freq:398625
/sys/devices/system/cpu/cpu3/cpufreq/scaling_cur_freq:399663
/sys/devices/system/cpu/cpu4/cpufreq/scaling_cur_freq:754962
/sys/devices/system/cpu/cpu5/cpufreq/scaling_cur_freq:397905
/sys/devices/system/cpu/cpu6/cpufreq/scaling_cur_freq:584914
/sys/devices/system/cpu/cpu7/cpufreq/scaling_cur_freq:403312
/sys/devices/system/cpu/cpu8/cpufreq/scaling_cur_freq:399085
/sys/devices/system/cpu/cpu9/cpufreq/scaling_cur_freq:398775

```Everything looks as though throttling is involved except for CPU 15. I do not understand this. I am not familiar with throttling methods on AMD processors so am unsure how to investigate further.

From your description, it sounds as though the powersave governor is successfully holding the CPU frequency at minimum (1.2GHz) and avoiding throttling.
For the next test I would suggest to try the ondemand frequency scaling governor, as it will allow increased CPU frequencies if the system needs it, but won't force it all the time as the performance governor does.

Your processor should be compatible with the amd-pstate CPU frequency scaling driver, so you might want to try it. (It should be the default on recent enough kernels, but I do not know if Ubuntu overrides the default or not, or if you are.)

---

### Post by Starcraftmazter on 2023-08-22
I put the amd-pstate in the kernel flags and it is being loaded, but it's not really doing anything. Overall, I am still getting the slowness issue, I think changing the governors was maybe an anecdotal thing that didn't really make any impact in the long-run.

There's a few things I need to sort out though, firstly I cannot get the grub menu to come up booting, and it's very annoying because it's making it hard to test things. This following is my grub config file, and I did the rebuild, but still no menu

```

GRUB_DEFAULT=0

GRUB_TIMEOUT_STYLE=countdown
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_pstate=passive"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

```

The other thing, I am on kernel 5.15 - however I read the amd pstate driver is in 5.17, I am wondering how can I upgrade? I am on kubuntu 22.04 LTS once more, but from reading, it should already be on a newer kernel - yet when I do an apt upgrade, there is no newer kernel installed. I am really confused by what's going on with that, any advice?

---

### Post by deadflowr on 2023-08-23
> The other thing, I am on kernel 5.15 - however I read the amd pstate driver is in 5.17, I am wondering how can I upgrade? I am on kubuntu 22.04 LTS once more, but from reading, it should already be on a newer kernel - yet when I do an apt upgrade, there is no newer kernel installed. I am really confused by what's going on with that, any advice?

Ubunut LTS can come with either a general availability kernel (like what you have which on 22.04 is 5.15)
or it can come with the hardware enablement stack kernel aka HWE (which is upgraded every point release ( currently the HWE kernel is 6.2).
More about HWE here:[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

To install the hwe kernel run
```
[sudo apt update
sudo apt install linux-generic-hwe-22.04
```
reboot.
Because it's newer and higher version, it should automatically boot into the newly installed kernel.


HWE kernels are based on the kernels used in the standard releases like what 23.04 and upcoming 23.10 releases use or will use.
They are updated around the same time as LTS point releases are made available.
Best estimate right now is the planned kernel for 23.10 will be the 6.5 series, which should land in late January early February.
Point releases land about half way between Ubuntu's releases. 
(Ubuntu's releases happen in April and October, hence the name scheme that all end in either .04 or .10,
so point releases usually land in July/August or January/February.

HWE kernels will upgrade until they ht the 5th point release, which will be based on whatever kernel will be used in the next LTS release.
After that HWE kernel will remain as that for the rest of the support for its lifetime.

---

### Post by Starcraftmazter on 2023-08-23
Thanks, after updating the kernel, there seem to be no weird stale cores, every single time I do a check, they are always very similar - 

```

cpu MHz         : 399.258
cpu MHz         : 400.000
cpu MHz         : 399.021
cpu MHz         : 400.000
cpu MHz         : 399.226
cpu MHz         : 399.217
cpu MHz         : 399.233
cpu MHz         : 400.000
cpu MHz         : 399.228
cpu MHz         : 399.076
cpu MHz         : 399.197
cpu MHz         : 399.147
cpu MHz         : 400.000
cpu MHz         : 399.121
cpu MHz         : 399.202
cpu MHz         : 400.000

```

or maybe at least the stale values are reflecting what the clock should be.

If I try and set the clocks using the CLI cpupower it doesn't seem to work, doesn't do anything. I also have cpupower-gui, that displays 400mhz, if I change it, it seems to work momentarily, before being downclocked to 400mhz again within 10-20 seconds. I am wondering if there is a way to lock the clocks? 

Do you think there could be any hardware problem reducing the clock speed?

---

### Post by Doug S on 2023-08-23
> **Starcraftmazter said:**
> Overall, I am still getting the slowness issue, I think changing the governors was maybe an anecdotal thing that didn't really make any impact in the long-run.
Well, show us the supporting data. And did it take longer, before throttling started? The purpose of the test was to avoid high temperatures and avoid engaging the last line of defence thermal throttling, which is typically a hardware induced Clock Modulation.

> **Starcraftmazter said:**
> 
There's a few things I need to sort out though, firstly I cannot get the grub menu to come up booting, and it's very annoying because it's making it hard to test things. This following is my grub config file, and I did the rebuild, but still no menu

```

GRUB_DEFAULT=0

GRUB_TIMEOUT_STYLE=countdown
GRUB_TIMEOUT=3   [COLOR="#FF0000"]<<< try a longer timeout, I use 10 seconds to give time for the screen to come up and such[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_pstate=passive"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console  [COLOR="#FF0000"]<<<< I have this commented out[/COLOR]

```


> **Starcraftmazter said:**
> If I try and set the clocks using the CLI cpupower it doesn't seem to work, doesn't do anything. I also have cpupower-gui, that displays 400mhz, if I change it, it seems to work momentarily, before being downclocked to 400mhz again within 10-20 seconds. I don't use cpupower, only direct primitive commands. It would be good to know all your basic settings via primitive inquiry as in previous posts.

> **Starcraftmazter said:**
> Do you think there could be any hardware problem reducing the clock speed?Yes. For example we know that some dell laptops force clock modulation on Intel processors if the user is not using a dell ac adapter. However, the "within 10-20 seconds" comment suggests that some throttling type daemon has either gone insane or you really have some thermal or power limit issue. Is thermald running? Is tlp running?

EDIT: An example of Clock Modulation on an Intel Processor (Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz):
(using turbostat, linux-tools-common package (I think)):

```
doug@s19:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 5
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
0.01    2416    297     31      2.01    1.36    0.00    1.33
0.01    3249    164     31      1.96    1.30    0.00    1.33
0.00    3532    122     31      2.02    1.36    0.00    1.33
0.01    1613    141     31      1.90    1.25    0.00    1.33
0.00    3395    114     31      1.92    1.27    0.00    1.33
0.01    2671    115     31      1.96    1.30    0.00    1.33
0.01    2539    150     31      1.95    1.30    0.00    1.33
0.01    2816    257     31      1.83    1.18    0.00    1.33
0.01    3075    132     31      1.86    1.20    0.00    1.33
0.10    671     272     31      1.98    1.32    0.00    1.33    [COLOR="#FF0000"]<<<<< Clock Modulation applied[/COLOR]
0.08    373     184     32      1.91    1.26    0.00    1.34
0.12    260     154     31      1.99    1.34    0.00    1.33
0.15    233     179     31      1.98    1.33    0.00    1.33
0.28    184     292     31      1.81    1.16    0.00    1.33
4.93    612     3141    34      9.58    8.92    0.00    1.37
8.76    644     5431    32      17.12   16.44   0.00    1.46   [COLOR="#FF0000"]<<<<< Load applied 100% on 1 CPU[/COLOR]
8.39    647     5158    32      16.73   16.05   0.00    1.48
8.38    647     5139    33      16.43   15.76   0.00    1.47
8.38    647     5145    32      16.71   16.03   0.00    1.48
8.39    647     5160    32      16.88   16.20   0.00    1.48
8.39    647     5296    33      16.76   16.08   0.00    1.48
8.44    648     5286    33      16.81   16.13   0.00    1.48
8.39    647     5166    33      17.03   16.36   0.00    1.48
8.39    647     5206    33      16.81   16.13   0.00    1.48
8.39    647     5230    34      16.70   16.02   0.00    1.47
8.43    3627    5288    46      23.99   23.20   0.00    2.31  [COLOR="#FF0000"]<<<<< Clock modulation disabled. [/COLOR]
8.32    4800    5188    45      26.60   25.75   0.00    2.63  [COLOR="#FF0000"]<<<<< Observe rise in Temperature and Power[/COLOR]
8.35    4800    5172    48      26.72   25.87   0.00    2.62
8.34    4800    5155    46      26.74   25.90   0.00    2.62
``` I have not been able to find anything about the subject for AMD processors.

---

### Post by Starcraftmazter on 2023-08-27
Just a bit of an update, it seems like using the powersave governor is the only thing that is working, it seems to have worked continuously after several days. Still not enough data as I need to sleep and restart laptop and try again, but for now I'm enjoying the speed.

```

cpu MHz         : 3200.000
cpu MHz         : 3168.550
cpu MHz         : 3168.517
cpu MHz         : 3168.512
cpu MHz         : 3200.000
cpu MHz         : 3159.225
cpu MHz         : 3200.000
cpu MHz         : 3168.881
cpu MHz         : 3168.510
cpu MHz         : 3200.000
cpu MHz         : 3168.815
cpu MHz         : 3200.000
cpu MHz         : 3200.000
cpu MHz         : 3200.000
cpu MHz         : 3200.000
cpu MHz         : 3168.397

```

The command I was referring to is the one mentioned earlier in the thread
```

sudo cpupower frequency-set -u 3200mhz
sudo cpupower frequency-set -d 3200mhz

```

I believe the UI does the same thing, it doesn't seem to stick for very long at all.

I am not sure if thermald or tlp is running - how would I check?

This is my this output

```

&#10140;  bin sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 5
Busy%   Bzy_MHz IRQ     CorWatt PkgWatt
1.79    3170    24962   1.29    5.46
0.97    3169    9882    1.11    4.20
1.66    3168    32548   0.83    5.67
1.24    3168    26523   0.78    5.39
2.67    3169    38732   1.83    6.05
0.86    3169    8779    1.04    4.05
0.94    3169    8399    1.23    4.04
0.79    3168    7341    1.14    3.88
1.39    3169    18136   1.29    4.39
0.80    3169    8068    1.17    4.15
1.05    3168    12825   0.97    4.84
1.39    3162    18711   0.85    5.42
1.10    3175    9966    1.26    4.19
0.81    3169    7021    1.11    4.01
1.52    3169    13795   1.26    4.65
0.79    3169    7573    1.03    4.14
0.90    3169    9273    1.10    4.29
0.91    3169    9147    1.08    4.32
0.84    3168    9297    1.08    4.32
0.88    3169    9223    1.15    4.25
0.84    3168    10124   1.05    4.60
1.65    3169    13906   1.24    5.09
0.92    3168    13185   1.06    4.90
2.89    3169    21729   1.68    5.54
0.79    3168    13032   0.89    4.94


```

---

### Post by Doug S on 2023-08-28
> **Starcraftmazter said:**
> I am not sure if thermald or tlp is running - how would I check?

Example:

```

doug@s19:~/prime95$ [COLOR="#FF0000"]sudo systemctl status thermald[/COLOR]
&#9679; thermald.service - Thermal Daemon Service
     Loaded: loaded (/lib/systemd/system/thermald.service; disabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-08-28 13:22:33 PDT; 2min 44s ago
   Main PID: 22582 (thermald)
      Tasks: 2 (limit: 38152)
     Memory: 2.5M
     CGroup: /system.slice/thermald.service
             &#9492;&#9472;22582 /usr/sbin/thermald --systemd --dbus-enable --adaptive

Aug 28 13:22:33 s19 systemd[1]: Starting Thermal Daemon Service...
Aug 28 13:22:33 s19 systemd[1]: Started Thermal Daemon Service.
Aug 28 13:22:33 s19 thermald[22582]: 22 CPUID levels; family:model:stepping 0x6:a5:5 (6:165:5)
Aug 28 13:22:33 s19 thermald[22582]: 22 CPUID levels; family:model:stepping 0x6:a5:5 (6:165:5)
Aug 28 13:22:33 s19 thermald[22582]: Polling mode is enabled: 4
Aug 28 13:22:33 s19 thermald[22582]: sensor id 5 : No temp sysfs for reading raw temp
Aug 28 13:22:33 s19 thermald[22582]: sensor id 5 : No temp sysfs for reading raw temp
Aug 28 13:22:33 s19 thermald[22582]: sensor id 5 : No temp sysfs for reading raw temp
Aug 28 13:22:33 s19 thermald[22582]: XML zone: invalid sensor type []
doug@s19:~/prime95$ [COLOR="#FF0000"]ps aux | grep thermald[/COLOR]
root       22582  0.0  0.0 126272  9328 ?        Ssl  13:22   0:00 [COLOR="#FF0000"]/usr/sbin/thermald[/COLOR] --systemd --dbus-enable --adaptive
doug       22630  0.0  0.0   9040   656 pts/0    R+   13:25   0:00 grep --color=auto thermald
doug@s19:~/prime95$

```I would assume similar for tlp, but I have never used it.
I normally have thermald disabled:

```
doug@s19:~$ [COLOR="#FF0000"]sudo systemctl status thermald[/COLOR]
&#9679; thermald.service - Thermal Daemon Service
     Loaded: loaded (/lib/systemd/system/thermald.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
```

---

### Post by Starcraftmazter on 2023-08-28
Mine says cpu not supported;

```

&#9675; thermald.service - Thermal Daemon Service
     Loaded: loaded (/lib/systemd/system/thermald.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Wed 2023-08-23 19:24:22 AEST; 5 days ago
   Main PID: 1014 (code=exited, status=0/SUCCESS)
        CPU: 53ms

Aug 23 19:24:22 moocow systemd[1]: Starting Thermal Daemon Service...
Aug 23 19:24:22 moocow thermald[1014]: Unsupported cpu model or platform
Aug 23 19:24:22 moocow systemd[1]: thermald.service: Deactivated successfully.
Aug 23 19:24:22 moocow systemd[1]: Started Thermal Daemon Service.


```

Is it something to worry about?

---

### Post by #&amp;thj^% on 2023-08-28
> **Starcraftmazter said:**
> 

Is it something to worry about?

Not necessarily, please see mine:
```
sudo systemctl status thermald
&#9675; thermald.service - Thermal Daemon Service
     Loaded: loaded (/lib/systemd/system/thermald.service; enabled; preset: ena>
     Active: inactive (dead) since Mon 2023-08-28 18:57:12 MDT; 5s ago
   Duration: 1ms
    Process: 797724 ExecStart=/usr/sbin/thermald --systemd --dbus-enable --adap>
   Main PID: 797724 (code=exited, status=0/SUCCESS)
        CPU: 10ms

Aug 28 18:57:12 lvm-lite systemd[1]: Starting thermald.service - Thermal Daemon>
Aug 28 18:57:12 lvm-lite systemd[1]: Started thermald.service - Thermal Daemon >
Aug 28 18:57:12 lvm-lite thermald[797724]: Unsupported cpu model or platform
Aug 28 18:57:12 lvm-lite systemd[1]: thermald.service: Deactivated successfu
```
But there's more: >(The K10 is the CPU)
```
sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +38.0°C  

nvme-pci-0200
Adapter: PCI adapter
Composite:    +35.9°C  (low  =  -5.2°C, high = +83.8°C)
                       (crit = +87.8°C)

nvme-pci-0400
Adapter: PCI adapter
Composite:    +28.9°C  (low  =  -5.2°C, high = +79.8°C)
                       (crit = +84.8°C)

BAT0-acpi-0
Adapter: ACPI interface
in0:          17.20 V  

```

---

### Post by Starcraftmazter on 2023-09-16
One thing I think I've discovered is, for whatever reason, the CPU seems to always be performing well when the laptop is started without being plugged into power. The combination of that and using ondemand seems to be generally working really well over the last few weeks.

---

