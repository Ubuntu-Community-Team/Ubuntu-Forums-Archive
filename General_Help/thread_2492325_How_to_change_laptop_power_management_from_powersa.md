---
title: "How to change laptop power management from powersave to performance"
date: 2023-11-07
forum: General Help
---

### Post by cedbarth on 2023-11-07
Hi,
I have a pcspecialist laptop with i7-1360P 32 Gb ram and 2Tb 990 pro nvm ssd and I have installed dual boot on this laptop, with Windows 11 pro and Ubuntu 22.04 LTS.
When I run passmark performance 11 test with ubuntu I get 13 000 score for CPU running it with Ubuntu where as I get 20800 running the same test with Windows 11.
The difference is so important that I guess the laptop performance is deliberately diminished by linux but don't know how to get the full performance of it.
In Settings menu, I have set Power mode to Performance, but if I type in a terminal cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor, I only get powersave as result.
I have tried to set /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor to performance but it doesn't work, sys/devices/system/cpu/cpu*/cpufreq/scaling_governor all stay equal to powersave
Any ideas ?
Thx a lot !

---

### Post by #&amp;thj^% on 2023-11-07
I do it through grub ie:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
performance
performance
performance
performance
performance
performance
performance
performance

```
my grub looks like this:
```
GRUB_CMDLINE_LINUX="cpufreq.default_governor=performance"

```
Just so your not confused, my whole grub reads as:
```
&#9492;&#9472;> tac /etc/default/grub
#GRUB_INIT_TUNE="480 440 1"
# Uncomment to get a beep at grub start

#GRUB_DISABLE_RECOVERY="true"
# Uncomment to disable generation of recovery mode menu entries

#GRUB_DISABLE_LINUX_UUID=true
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux

#GRUB_GFXMODE=640x480
# you can see them in real GRUB with the command `vbeinfo'
# note that you can use only modes which your graphic card supports via VBE
# The resolution used on graphical terminal

#GRUB_TERMINAL=console
# Uncomment to disable graphical terminal (grub-pc only)

#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
# This works with Linux (no patch required) and with any kernel that obtains
# Uncomment to enable BadRAM filtering, modify to suit your needs

GRUB_BACKGROUND="/boot/grub_linux_lite.png"
# Linux Lite Grub background

[COLOR="#FF0000"]GRUB_CMDLINE_LINUX="cpufreq.default_governor=performance"[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR='Linux Lite'
GRUB_TIMEOUT=10
GRUB_TIMEOUT_STYLE=hidden
GRUB_DEFAULT=0

#   info -f grub -n 'Simple configuration'
# For full documentation of the options in this file, see:
# /boot/grub/grub.cfg.
# If you change this file, run 'update-grub' afterwards to update

```
EDIT: this might make your CPU run a few degrees hotter/warmer so keep a good eye on it, and you can always undo that change very quickly.
FTR: My CPU "Intel Core i5-10210U"

---

### Post by MAFoElffen on 2023-11-07
Easier:

3 other, of the many ways to do that... In Ubuntu, in the Gnome top Bar > The right of that bar is what Gnome calls the "System Menu". You proably select that to turm off your laptop... Notice that right below the battery power line of the drop-down is your Power Settings... Click on the Arrow Icon on the left of that... It will display the power modes available... Select one.

If you use that same, and go to "Settings' > Power... Same.  

Form a command line
```

poerprofilesctl list
powerprofilesctl set <power_profile>

```
*** VERY IMPORTANT ***
Don't get greedy...

What I mean by that, some laptops do not have "Performance" available as a valid profile. [COLOR=#ff0000]_Do not set it to "performance" if it is not listed._[/COLOR]

It can be done, but it is not a good idea at all!!! That will break your gnome-settings manager, and it will not start after that after that. It will just continually crash that app, until you set that option back to something valid. I know. I forced it into that mode. Yes, I did that and had to recover from that mistake. Learn from my mistake on that.

---

### Post by cedbarth on 2023-11-08
> **1fallen said:**
> I do it through grub ie:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
performance
performance
performance
performance
performance
performance
performance
performance

```
my grub looks like this:
```
GRUB_CMDLINE_LINUX="cpufreq.default_governor=performance"

```
Just so your not confused, my whole grub reads as:
```
&#9492;&#9472;> tac /etc/default/grub
#GRUB_INIT_TUNE="480 440 1"
# Uncomment to get a beep at grub start

#GRUB_DISABLE_RECOVERY="true"
# Uncomment to disable generation of recovery mode menu entries

#GRUB_DISABLE_LINUX_UUID=true
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux

#GRUB_GFXMODE=640x480
# you can see them in real GRUB with the command `vbeinfo'
# note that you can use only modes which your graphic card supports via VBE
# The resolution used on graphical terminal

#GRUB_TERMINAL=console
# Uncomment to disable graphical terminal (grub-pc only)

#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
# This works with Linux (no patch required) and with any kernel that obtains
# Uncomment to enable BadRAM filtering, modify to suit your needs

GRUB_BACKGROUND="/boot/grub_linux_lite.png"
# Linux Lite Grub background

[COLOR=#FF0000]GRUB_CMDLINE_LINUX="cpufreq.default_governor=performance"[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR='Linux Lite'
GRUB_TIMEOUT=10
GRUB_TIMEOUT_STYLE=hidden
GRUB_DEFAULT=0

#   info -f grub -n 'Simple configuration'
# For full documentation of the options in this file, see:
# /boot/grub/grub.cfg.
# If you change this file, run 'update-grub' afterwards to update

```
EDIT: this might make your CPU run a few degrees hotter/warmer so keep a good eye on it, and you can always undo that change very quickly.
FTR: My CPU "Intel Core i5-10210U"

Hi,
Thanks for your help
I have edited /etc/default/grub and run update-grub before rebooting
Unfortunately that doesn't change the result of 
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
This still results only in powersave :sad: 
I've run then the benchmark test that still results in a bad score around 14000 in comparison with Windows score ( 20800 )

> **MAFoElffen said:**
> Easier:

3 other, of the many ways to do that... In Ubuntu, in the Gnome top Bar > The right of that bar is what Gnome calls the "System Menu". You proably select that to turm off your laptop... Notice that right below the battery power line of the drop-down is your Power Settings... Click on the Arrow Icon on the left of that... It will display the power modes available... Select one.

If you use that same, and go to "Settings' > Power... Same.  

Form a command line
```

poerprofilesctl list
powerprofilesctl set <power_profile>

```
*** VERY IMPORTANT ***
Don't get greedy...

What I mean by that, some laptops do not have "Performance" available as a valid profile. [COLOR=#ff0000]_Do not set it to "performance" if it is not listed._[/COLOR]

It can be done, but it is not a good idea at all!!! That will break your gnome-settings manager, and it will not start after that after that. It will just continually crash that app, until you set that option back to something valid. I know. I forced it into that mode. Yes, I did that and had to recover from that mistake. Learn from my mistake on that.
Hi,
Thanks for your help
The way that you told me was the way I tried first to change power mode  using gnome top-bar and even though performance mode is proposed, it  doesn't change anything when set as performance mode as the benchmark  scores are bad and typing command cat  /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor results only in  powersave for every cpu core. I've also tried the command line version  you stated and same results

---

### Post by kc1di on 2023-11-08
You might want to give slimbook Battery a try found here:
[https://slimbook.es/en/tutoriales/aplicaciones-slimbook/520-slimbook-battery-4-application-to-optimize-your-laptop-s-battery]("https://slimbook.es/en/tutoriales/aplicaciones-slimbook/520-slimbook-battery-4-application-to-optimize-your-laptop-s-battery")

---

### Post by cedbarth on 2023-11-08
> **kc1di said:**
> You might want to give slimbook Battery a try found here:
[https://slimbook.es/en/tutoriales/aplicaciones-slimbook/520-slimbook-battery-4-application-to-optimize-your-laptop-s-battery](https://slimbook.es/en/tutoriales/aplicaciones-slimbook/520-slimbook-battery-4-application-to-optimize-your-laptop-s-battery)

Hi,thanks for your help,
I've installed the app and rebooted the laptop but unfortunately, it doesn't change the benchmark score nor does it change the result of
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor still powersave even if I set power mode to Maximul performance using slimbattery.
There must be a process that constantly sets power mode to powersave, but which ???

Maybe it's better to move this topic to hardware section actually, isn't it ?

---

### Post by #&amp;thj^% on 2023-11-08
Might check with:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```
To see if it's available, please show us that.
This is a Valid warning:
> What I mean by that, some laptops do not have "Performance" available as a valid profile. Do not set it to "performance" if it is not listed.


---

### Post by Doug S on 2023-11-08
> **cedbarth said:**
> When I run passmark performance 11 test with ubuntu I get 13 000 score for CPU running it with Ubuntu where as I get 20800 running the same test with Windows 11. That is really interesting and worthy of looking deeper, as you are attempting to do.

I am a server person and never run any of these secondary performance manipulation utilities. I do not know what is overriding your attempts to set the performance governor. Perhaps another method would be to accept the use of the seemingly forced powersave governor, but set the minimum CPU frequency to be the maximum. You could also manually set EPP (energy performance preference).

Example (I am assuming the intel_pstate CPU frequency scaling driver, HWP enabled):

```
doug@s19:~/tmp/geo$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/intel_pstate/*_perf_pct[/COLOR]
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/[COLOR="#FF0000"]min_perf_pct:16[/COLOR]
doug@s19:~/tmp/geo$ [COLOR="#FF0000"]echo 100 | sudo tee /sys/devices/system/cpu/intel_pstate/min_perf_pct[/COLOR]
100
doug@s19:~/tmp/geo$ grep . /sys/devices/system/cpu/intel_pstate/*_perf_pct
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/[COLOR="#FF0000"]min_perf_pct:100[/COLOR]
```

I simultaneously monitoring with turbostat:

```
doug@s19:~/c$ [COLOR="#FF0000"]sudo turbostat --quiet --Summary --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 15[/COLOR]
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
0.06    3020    1090    35      1.44    0.77    0.00    1.33
0.06    2999    1103    36      1.45    0.79    0.00    1.33
0.02    [COLOR="#FF0000"]1884[/COLOR]    720     35      1.53    0.87    0.00    1.33
0.04    [COLOR="#FF0000"]4800[/COLOR]    819     35      1.54    0.88    0.00    1.33
0.04    4800    872     36      1.58    0.91    0.00    1.33
^C0.00  4801    310     36      1.54    0.88    0.00    1.33
doug@s19:~/c$
```

And:

```
doug@s19:~/tmp/geo$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpufreq/policy5/energy_performance_*[/COLOR]
/sys/devices/system/cpu/cpufreq/policy5/energy_performance_available_preferences:default performance balance_performance balance_power power
/sys/devices/system/cpu/cpufreq/policy5/energy_performance_preference:balance_performance
doug@s19:~/tmp/geo$ grep . /sys/devices/system/cpu/cpufreq/policy*/energy_performance_preference
/sys/devices/system/cpu/cpufreq/policy0/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy10/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy11/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy1/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy2/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy3/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy4/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy5/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy6/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy7/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy8/energy_performance_preference:balance_performance
/sys/devices/system/cpu/cpufreq/policy9/energy_performance_preference:balance_performance
doug@s19:~/tmp/geo$ [COLOR="#FF0000"]echo performance | sudo tee /sys/devices/system/cpu/cpufreq/policy*/energy_performance_preference[/COLOR]
performance
doug@s19:~/tmp/geo$ grep . /sys/devices/system/cpu/cpufreq/policy*/energy_performance_preference
/sys/devices/system/cpu/cpufreq/policy0/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy10/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy11/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy1/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy2/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy3/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy4/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy5/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy6/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy7/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy8/energy_performance_preference:performance
/sys/devices/system/cpu/cpufreq/policy9/energy_performance_preference:performance

```

My input to your investigation is: Try to determine what the test is actually doing and pick away at it trying to isolate the parts that really differ between windows and linux; Try the intel_cpufreq CPU frequency scaling driver (i.e. the intel_pstate driver in passive mode); Try with HWP (Hardware Pstate Control) disabled; Try the acpi_cpufreq CPU frequency scaling driver; Examine your available idle states, and try disabling some; The default idle governor is "menu", try "teo". Watch everything with turbostat.

From another thread I have been trying to help with, it seems that windows and Ubuntu linux might default to different maximum processor temperatures before throttling. That might be another avenue of investigation.

---

### Post by cedbarth on 2023-11-08
> **1fallen said:**
> Might check with:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```
To see if it's available, please show us that.
This is a Valid warning:
Hi,
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
performance powersave

```

Hi Doug,
Thanks for all your ideas and hints !
Unfortunately, up to now I have not been successful ...
I've tried to set /sys/devices/system/cpu/intel_pstate/min_perf_pct to 100 ( initial value 9) but it went back shortly after to 9, the same occurred with /sys/devices/system/cpu/cpufreq/policy*/energy_performance_preference.
Therefore I tried with intel_pstate passive and HWP disabled using this grub entry in /etc/default/grub :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=210e6663-6539-42ea-820e-8902c7791b0f resume_offset=13074432 ipv6.disable=1 consoleblank=450 intel_pstate=passive intel_pstate=no_hwp cpufreq.default_governor=schedutil msr.allow_writes=on cpuidle.governor=teo"

But then I can't disable ondemand cpu state, if I set it to performance 3 seconds later it is set back to ondemand.
I don't get better benchmark scores than 16000, still quite far from 21 000 ...

There are a lot of different cpu test categories that do better running with windows 11 than with ubuntu.
Here are the windows11 / Ubuntu subcategories scores:
                                                                               W11 / Linux 
Integer Math Mops/s                                               75000/83000 [COLOR=#00ff00]+10%[/COLOR]
Floating point Math Mops/s                                     51000/37900  [COLOR=#ff0000]-26%[/COLOR]
Prime Numbers Primes Millions/s                                 96/72         [COLOR=#ff0000]-25%[/COLOR]
Sorting ( Thousand strings/s)                                25200/23500    [COLOR=#ff0000]-7%[/COLOR]
Encryption (MB/s)                                                14000/11000    [COLOR=#ff0000]-22%[/COLOR]
Compression (KB/s)                                            23600/16500     [COLOR=#ff0000]-30%[/COLOR]
CPU single Threaded (Mops/s)                               3700/1800      [COLOR=#ff0000] -52%[/COLOR]
Physics (Frames/s )                                              1600/1600       0%
Extended Instructions (SSE) (Million Matrices /s ) 13200/7700       [COLOR=#ff0000]-42%[/COLOR]

---

### Post by Doug S on 2023-11-08
EDIT: I had not seen the edit to your prior post, as I it took me so long to write this post. But aghhh, I see the single threaded test is indeed a bad one:

Thanks for your reply and for trying the suggestions. I do not know what service might be overriding these settings. Very annoying. If whatever it is can be disabled, then some progress can be made.

I am not familiar with the PassMark tests, but I did see some stuff on their web page. One thing that caught my eye was "CPU Single Threaded". Depending on how that test is implemented (i.e. if it is done with a high rate of new PIDs with time), the intel_pstate CPU frequency scaling driver using the powersave scaling governor can give very poor results.

Example (shorter overall job time is better):

intel_pstate, powersave, HWP enabled: 3 minutes 41.2 seconds;  Approx 220 processes per second; 3.8 watts processor power.
intel_pstate, powersave, HWP enabled, CPU affinity forced to CPU 5 (even better than performance gov for this test): 1 minute 28.2 seconds; 567 processes per second; 24.9 watts processor power.
intel_pstate, performance, HWP enabled: 1 minute 31.4 seconds; 547.5 processes per second; 26.7 watts processor power.

---

### Post by MAFoElffen on 2023-11-08
> **cedbarth said:**
> 
```

W11 / Linux 
Integer Math Mops/s                                               75000/83000 [COLOR=#00ff00]+10%[/COLOR]
Floating point Math Mops/s                                     51000/37900  [COLOR=#ff0000]-26%[/COLOR]
Prime Numbers Primes Millions/s                                 96/72         [COLOR=#ff0000]-25%[/COLOR]
Sorting ( Thousand strings/s)                                25200/23500    [COLOR=#ff0000]-7%[/COLOR]
Encryption (MB/s)                                                14000/11000    [COLOR=#ff0000]-22%[/COLOR]
Compression (KB/s)                                            23600/16500     [COLOR=#ff0000]-30%[/COLOR]
CPU single Threaded (Mops/s)                               3700/1800      [COLOR=#ff0000] -52%[/COLOR]
Physics (Frames/s )                                              1600/1600       0%
Extended Instructions (SSE) (Million Matrices /s ) 13200/7700       [COLOR=#ff0000]-42%[/COLOR]

```

Hmmm. This thread is getting more and more interesting now.

Here is my workstation. It is set to performance:
```

13th Gen Intel(R) Core(TM) i9-13900K (x86_64)
16 cores @ 5500 MHz  |  125.6 GiB RAM
Number of Processes: 32  |  Test Iterations: 1  |  Test Duration: Medium
--------------------------------------------------------------------------
CPU Mark:                          57932
  Integer Math                     195916 Million Operations/s
  Floating Point Math              147948 Million Operations/s
  Prime Numbers                    182 Million Primes/s
  Sorting                          90427 Thousand Strings/s
  Encryption                       54542 MB/s
  Compression                      758 MB/s
  CPU Single Threaded              4789 Million Operations/s
  Physics                          2944 Frames/s
  Extended Instructions (SSE)      42385 Million Matrices/s

```
I queried the number of threads (32) and the sysfs: cpu max_freq (5500000)... And ran this to set all my threads to their max
```

sudo su -
for ((i=0; i<32; i++))
do
    echo 5500000 > /sys/devices/system/cpu/cpufreq/policy$i/scaling_min_freq
done

```
Which resulted in this
```

mafoelffen@msi-ubuntu:~/Passmark$ grep . /sys/devices/system/cpu/cpufreq/policy*/scaling_min_freq
/sys/devices/system/cpu/cpufreq/policy0/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy10/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy11/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy12/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy13/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy14/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy15/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy16/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy17/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy18/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy19/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy1/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy20/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy21/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy22/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy23/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy24/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy25/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy26/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy27/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy28/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy29/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy2/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy30/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy31/scaling_min_freq:4300000
/sys/devices/system/cpu/cpufreq/policy3/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy4/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy5/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy6/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy7/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy8/scaling_min_freq:5500000
/sys/devices/system/cpu/cpufreq/policy9/scaling_min_freq:5500000

```
Which then tested out as this:
```

13th Gen Intel(R) Core(TM) i9-13900K (x86_64)
16 cores @ 5500 MHz  |  125.6 GiB RAM
Number of Processes: 32  |  Test Iterations: 1  |  Test Duration: Medium
--------------------------------------------------------------------------
CPU Mark:                          58740
  Integer Math                     219828 Million Operations/s
  Floating Point Math              148031 Million Operations/s
  Prime Numbers                    181 Million Primes/s
  Sorting                          90860 Thousand Strings/s
  Encryption                       54213 MB/s
  Compression                      780 MB/s
  CPU Single Threaded              4770 Million Operations/s
  Physics                          2840 Frames/s
  Extended Instructions (SSE)      42098 Million Matrices/s

```
That is not much of an increase there, and... IDK. That is an unlocked 13th Gen i9, and I'm nowhere close to 83000 with Passmark... Like you are getting. I'm not sure how it calculates that benchmark... Hmmm.

---

### Post by Doug S on 2023-11-08
> **MAFoElffen said:**
> Hmmm. This thread is getting more and more interesting now. It really is. Thanks for your tests. With your much higher TDP (thermal design power), I would expect your processor to blow cedbarth's away and it does.
I would be very interested in your results with your governor set to powersave.

> **MAFoElffen said:**
> 
```

sudo su -
for ((i=0; i<32; i++))
do
    echo 5500000 > /sys/devices/system/cpu/cpufreq/policy$i/scaling_min_freq
done

```
 You do not need to do a for loop anymore. This will do it all:

```
echo 5500000 | sudo tee /sys/devices/system/cpu/cpufreq/policy*/scaling_min_freq
```Anyway, that was just a work around attempt suggestion for inability to set the performance governor. You don't need it.


> **MAFoElffen said:**
> That is not much of an increase there, and... IDK. That is an unlocked 13th Gen i9, and I'm nowhere close to 83000 with Passmark... Like you are getting. I'm not sure how it calculates that benchmark... Hmmm.
??
You get: 57932 and 58740
cedbarth gets: 13000 on Ubuntu and 20800 on Windows.

Edit: Oh gosh. Somehow I thought one had to pay to use PassMark. I didn't know I could just download it and run it as a cli on my test server. It is windows users that have to pay for it:

Performance:
```
                   PassMark PerformanceTest Linux (11.0.1002)
Intel Core i5-10600K CPU @ 4.10GHz (x86_64)
6 cores @ 4800 MHz  |  31.2 GiB RAM
Number of Processes: 12  |  Test Iterations: 1  |  Test Duration: Medium
--------------------------------------------------------------------------------
CPU Mark:                          17056
  Integer Math                     53044 Million Operations/s
  Floating Point Math              32628 Million Operations/s
  Prime Numbers                    58.2 Million Primes/s
  Sorting                          31976 Thousand Strings/s
  Encryption                       7300 MB/s
  Compression                      239653 KB/s
  CPU Single Threaded              3167 Million Operations/s
  Physics                          1088 Frames/s
  Extended Instructions (SSE)      12932 Million Matrices/s
```

Powersave:
```
                   PassMark PerformanceTest Linux (11.0.1002)
Intel Core i5-10600K CPU @ 4.10GHz (x86_64)
6 cores @ 4800 MHz  |  31.2 GiB RAM
Number of Processes: 12  |  Test Iterations: 1  |  Test Duration: Medium
--------------------------------------------------------------------------------
CPU Mark:                          17097
  Integer Math                     52941 Million Operations/s
  Floating Point Math              32628 Million Operations/s
  Prime Numbers                    57.8 Million Primes/s
  Sorting                          32300 Thousand Strings/s
  Encryption                       7329 MB/s
  Compression                      242445 KB/s
  CPU Single Threaded              3177 Million Operations/s
  Physics                          1093 Frames/s
  Extended Instructions (SSE)      12861 Million Matrices/s
```

EDIT 2: I ran a longer test, so that I could monitor with turbostat. Governor was powersave:

```
doug@s19:~/passmark/PerformanceTest$ cat results_cpu.yml
BaselineInfo:
  WebDBID: -1
  TimeStamp: 20231109042240
Version:
  Major: 11
  Minor: 0
  Build: 1002
  SpecialBuildName: ""
  ptArchitecture: x86_64_linux
Results:
  Results Complete: true
  NumTestProcesses: 12
  CPU_INTEGER_MATH: 53060.208480000008
  CPU_FLOATINGPOINT_MATH: 32615.910371909566
  CPU_PRIME: 58.000395482095996
  CPU_SORTING: 32129.477156627829
  CPU_ENCRYPTION: 7314.9562149714056
  CPU_COMPRESSION: 238923.00366760563
  CPU_SINGLETHREAD: 3149.3044110167989
  CPU_PHYSICS: 1112.1326643531979
  CPU_MATRIX_MULT_SSE: 12537.061784205227
  CPU_mm: 1543.4980639874607
  CPU_sse: 5796.434825367387
  CPU_fma: 18631.758576998032
  CPU_avx: 13182.991950250263
  CPU_avx512: 0
  m_CPU_enc_SHA: 2384141008.5737963
  m_CPU_enc_AES: 18486627293.57296
  m_CPU_enc_ECDSA: 2140094282.0628197
  ME_ALLOC_S: 0
  ME_READ_S: 0
  ME_READ_L: 0
  ME_WRITE: 0
  ME_LARGE: 0
  ME_LATENCY: 0
  ME_THREADED: 0
  SUMM_CPU: 17010.872487523346
  SUMM_ME: 0
SystemInformation:
  OSName: Ubuntu 20.04.6 LTS
  Kernel: 6.6.0-stock
  Device: ""
  Processor: Intel Core i5-10600K CPU @ 4.10GHz
  NumSockets: 1
  Manufacturer: GenuineIntel
  NumCores: 6
  NumLogicals: 12
  CPUFrequency: 4800
``` And:

```
doug@s19:~/idle/teo/util/pid-per-sec$ sudo /home/doug/kernel/linux/tools/power/x86/turbostat/turbostat --quiet --Summary --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 5
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
0.03    800     212     37      1.34    0.67    0.00    1.33
0.08    2544    417     37      1.44    0.77    0.00    1.34
89.37   4799    54064   61      70.00   69.35   0.00    1.34
99.76   4800    60555   61      76.15   75.50   0.00    1.33
99.74   4800    60463   62      78.42   77.77   0.00    1.34
99.76   4800    60148   62      76.67   76.01   0.00    1.33
99.74   4800    60174   63      78.12   77.46   0.00    1.33
99.76   4800    60195   63      76.83   76.17   0.00    1.34
99.74   4800    60545   63      78.48   77.82   0.00    1.34
99.76   4800    60147   63      77.18   76.51   0.00    1.34
99.74   4800    60185   64      78.11   77.45   0.00    1.34
99.76   4800    60165   64      78.17   77.51   0.00    1.33
99.76   4800    60509   65      77.51   76.85   0.00    1.33
99.74   4800    60214   61      76.46   75.81   0.00    1.34
99.76   4800    60226   60      73.93   73.27   0.00    1.33
99.74   4800    60180   60      76.18   75.52   0.00    1.34
99.76   4800    60140   60      74.05   73.40   0.00    1.33
99.73   4800    60519   61      76.20   75.55   0.00    1.34
99.76   4800    60149   61      74.12   73.45   0.00    1.33
99.74   4800    60182   62      76.67   76.01   0.00    1.34
99.76   4800    60141   62      74.43   73.77   0.00    1.33
99.73   4800    60514   68      75.72   75.06   0.00    1.34
99.76   4800    60163   63      75.83   75.18   0.00    1.33
99.76   4800    60178   63      74.58   73.93   0.00    1.33
99.74   4800    60226   62      70.13   68.53   0.00    4.35
99.76   4800    60132   61      65.38   63.35   0.00    5.72
66.13   4800    41675   61      68.63   67.05   0.00    4.46
49.95   4800    31942   60      69.42   67.72   0.00    5.11
70.45   4800    43556   59      71.49   69.94   0.00    4.37
99.76   4800    60187   60      64.99   62.98   0.00    5.68
90.05   4800    55378   66      67.13   65.35   0.00    4.93
49.94   4800    31890   62      69.38   67.70   0.00    4.99
49.94   4800    31829   63      69.37   67.66   0.00    5.13
95.30   4800    57638   67      68.68   67.00   0.00    4.61
99.76   4800    60200   64      65.26   63.23   0.00    5.70
65.16   4800    41186   64      69.42   67.84   0.00    4.49
49.94   4800    31776   62      69.85   68.13   0.00    5.14
72.63   4800    44814   61      71.65   70.11   0.00    4.42
99.76   4800    60358   61      65.70   63.67   0.00    5.70
87.63   4800    53971   66      67.81   66.09   0.00    4.73
49.95   4800    31871   65      69.70   67.97   0.00    5.16
50.01   4800    31942   69      69.87   68.16   0.00    5.14
98.55   4800    59569   67      69.58   67.86   0.00    4.72
99.76   4800    60236   64      65.93   63.90   0.00    5.71
62.26   4800    39655   63      69.93   68.35   0.00    4.48
49.94   4800    31818   65      70.13   68.42   0.00    5.13
75.40   4792    46480   75      81.89   80.49   0.00    4.02
99.60   4768    60259   75      98.01   96.52   0.00    4.32
98.89   4777    60435   76      96.29   94.97   0.00    3.70
99.74   4798    60143   75      100.53  99.05   0.00    4.33
98.89   4799    59766   73      99.81   98.37   0.00    4.18
99.76   4800    60273   74      98.06   96.72   0.00    3.84
99.76   4800    60173   74      101.48  99.98   0.00    4.38
98.69   4800    59995   73      96.08   94.79   0.00    3.64
99.76   4800    60141   74      100.63  99.14   0.00    4.35
99.22   4800    59953   74      97.18   95.88   0.00    3.69
99.76   4800    60139   73      100.81  99.31   0.00    4.37
98.64   4800    59991   74      97.63   96.40   0.00    3.53
99.66   4767    60162   75      100.17  99.39   0.00    2.22
99.45   4712    60149   71      96.41   95.78   0.00    1.49
99.69   4788    60170   75      100.18  99.40   0.00    2.33
99.56   4735    60508   75      99.76   99.13   0.00    1.50
99.45   4792    60096   75      98.60   97.82   0.00    2.31
99.56   4772    60284   75      101.92  101.29  0.00    1.50
99.33   4782    60055   73      98.46   97.71   0.00    2.12
99.72   4796    60158   75      102.75  102.08  0.00    1.75
99.04   4779    60287   72      98.90   98.21   0.00    1.82
99.76   4800    60176   74      102.77  102.05  0.00    2.01
99.46   4787    60148   72      100.72  100.06  0.00    1.48
99.76   4800    60193   73      105.58  104.93  0.00    1.61
99.37   4800    60344   74      105.40  104.75  0.00    1.61
98.91   4800    59760   74      101.43  100.77  0.00    1.56
99.76   4800    60143   74      106.48  105.84  0.00    1.63
97.50   4800    59082   73      100.42  99.77   0.00    1.55
99.76   4800    60150   74      105.81  105.16  0.00    1.62
97.61   4800    59525   72      100.10  99.44   0.00    1.55
99.76   4800    60154   74      105.71  105.06  0.00    1.62
98.32   4800    59497   72      101.32  100.67  0.00    1.56
99.76   4800    60193   74      105.63  104.96  0.00    1.62
99.34   4800    60330   74      105.94  105.29  0.00    1.62
9.87    4800    8100    61      28.21   27.55   0.00    1.37
8.35    4800    6767    63      29.55   28.88   0.00    1.42
7.14    4790    5761    54      22.18   21.52   0.00    1.34
8.35    4800    7084    63      29.32   28.65   0.00    1.45
7.25    4783    6546    55      23.03   22.37   0.00    1.34
8.34    4800    6026    63      27.66   26.99   0.00    1.45
7.18    4791    5401    55      23.71   23.05   0.00    1.34
8.32    4800    5374    62      26.83   26.16   0.00    1.44
7.36    4791    6210    59      24.88   24.21   0.00    1.35
8.35    4800    7068    62      25.97   25.31   0.00    1.40
7.44    4798    6045    45      25.86   25.19   0.00    1.39
96.79   4799    58436   63      81.08   79.40   0.00    4.76
99.76   4800    60545   69      86.43   84.43   0.00    5.87
98.68   4800    59977   71      85.96   84.25   0.00    4.89
99.76   4800    60169   72      87.04   85.02   0.00    5.92
98.77   4800    59685   73      86.74   85.01   0.00    4.94
99.76   4800    60165   65      84.80   82.81   0.00    5.79
99.21   4800    60320   74      87.76   86.08   0.00    4.84
99.75   4799    60159   72      84.64   82.60   0.00    5.90
99.75   4799    60180   72      88.69   86.62   0.00    6.09
98.13   4798    59436   70      84.62   82.94   0.00    4.75
99.74   4790    60513   71      87.79   85.75   0.00    5.99
99.26   4708    60009   75      92.67   91.63   0.00    2.63
99.55   4524    60164   75      101.80  101.14  0.00    1.33
99.57   4603    60203   75      101.35  100.69  0.00    1.34
99.58   4619    60146   75      101.33  100.68  0.00    1.33
99.68   4554    60549   76      108.95  108.30  0.00    1.33
99.67   4703    60210   75      99.20   98.52   0.00    1.34
99.56   4580    60178   75      109.43  108.78  0.00    1.33
99.62   4682    60162   75      103.83  103.17  0.00    1.34
99.52   4665    60521   76      108.80  108.15  0.00    1.33
99.53   4635    60191   70      110.29  109.63  0.00    1.34
99.55   4759    60272   75      105.55  104.89  0.00    1.33
99.70   4631    60164   75      117.37  116.71  0.00    1.33
28.61   4644    17633   43      34.50   33.83   0.00    1.34
0.14    800     585     43      1.97    1.31    0.00    1.33
0.02    800     168     43      1.95    1.29    0.00    1.33
0.02    800     151     43      1.89    1.23    0.00    1.33
0.02    800     155     43      1.78    1.12    0.00    1.33
0.13    3726    565     44      2.08    1.43    0.00    1.33
0.02    800     159     43      1.92    1.27    0.00    1.33
```Conclusions: Powersave/performance makes no difference because all CPUs are max'd out anyhow; I never hit power limit throttling, but the OP would have; I have a low processor temperature limit of 75 degrees C, and I did get thermal limit throttling, and would expect the OP would have also.

---

### Post by MAFoElffen on 2023-11-08
LOL. Dang. Yes. that makes sense now.

Mine is default at driver: intel_pstate... Rebooted, then set the power profile to power-saver...

I really think PassMark lies. LOL. Look at the results:
```

13th Gen Intel(R) Core(TM) i9-13900K (x86_64)
16 cores @ 5500 MHz  |  125.6 GiB RAM
Number of Processes: 32  |  Test Iterations: 1  |  Test Duration: Medium
--------------------------------------------------------------------------
CPU Mark:                          59367
  Integer Math                     220655 Million Operations/s
  Floating Point Math              146698 Million Operations/s
  Prime Numbers                    183 Million Primes/s
  Sorting                          90670 Thousand Strings/s
  Encryption                       54101 MB/s
  Compression                      779 MB/s
  CPU Single Threaded              4784 Million Operations/s
  Physics                          3032 Frames/s
  Extended Instructions (SSE)      44007 Million Matrices/s

```
How did it test out faster in a power-saver profile mode?

Continued in next post...

---

### Post by MAFoElffen on 2023-11-08
This is sysbench in "Performance"
```

mafoelffen@msi-ubuntu:~$ sysbench --threads=32 cpu run
sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3)

Running the test with following options:
Number of threads: 32
Initializing random number generator from current time


Prime numbers limit: 10000

Initializing worker threads...

Threads started!

CPU speed:
    events per second: 107406.68

General statistics:
    total time:                          10.0004s
    total number of events:              1074176

Latency (ms):
         min:                                    0.21
         avg:                                    0.30
         max:                                   24.24
         95th percentile:                        0.40
         sum:                               319869.19

Threads fairness:
    events (avg/stddev):           33568.0000/8001.95
    execution time (avg/stddev):   9.9959/0.00

```
This is sybench in "power-saver"
```

mafoelffen@msi-ubuntu:~$ sysbench --threads=32 cpu run
sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3)

Running the test with following options:
Number of threads: 32
Initializing random number generator from current time


Prime numbers limit: 10000

Initializing worker threads...

Threads started!

CPU speed:
    events per second: 106091.21

General statistics:
    total time:                          10.0003s
    total number of events:              1061030

Latency (ms):
         min:                                    0.21
         avg:                                    0.30
         max:                                   20.24
         95th percentile:                        0.40
         sum:                               319896.52

Threads fairness:
    events (avg/stddev):           33157.1875/8464.14
    execution time (avg/stddev):   9.9968/0.00

```
Performance tested faster...

---

### Post by Doug S on 2023-11-08
> **MAFoElffen said:**
> How did it test out faster in a power-saver profile mode? I doubt that it is. Repeat the test 10 or 20 times and I suspect you will observe enough run to run variability to explain it.

Example from my test server: 17097, 17067, 16982, 17009, 16968, 16933, 16882, 16925
The overall downward tend is due to my water cooled system heating up leading to more thermal throttling per test run. But run to run variability can still be observed, in addition to the trend.

---

### Post by MAFoElffen on 2023-11-09
More tests (tomorrow)... Consistency....

That is why I like phoronix-test-suite... Cross platform... That is what I usually use for benchmarking. And if it see's something that might be as out-of-the-norm, it will run that test over again to recheck it.  

@Doug S -- It can also be setup for system monitoring. Which I think that is something I think might be very helpful to you in tracking the kinds of things, with  what "you do", and test. 
> 
[h=3]System Monitoring[/h]            Through another Phoronix Test Suite module it is possible  to log in real-time various system sensors like the CPU temperature, the  battery power consumption, disk read/write speeds, and numerous other  sensors. This can be done while any test profile is running and the  recorded results are then provided within the results viewer. It is as  simple as running a command such as *MONITOR=all* phoronix-test-suite benchmark x264.



---

### Post by Doug S on 2023-11-09
I did the passmark test again, and uploaded my results. When comparing to windows computers with the same processor, my test Ubuntu linux computer was right in the mix (3rd out of 11 reports, the other 10 were windows).

Reference: [https://www.passmark.com/baselines/V11/display.php?id=505074020503](https://www.passmark.com/baselines/V11/display.php?id=505074020503)

Yes, I am big fan of the phoronix-test-suite. I run it from a git clone from the master. I did not know about the "system monitoring" option.

Now, for cedbarth's issue, and with all we have learned in the last day: I suspect excessive thermal throttling, maybe brought on by hitting to high of a processor temperature, or by an excessively low limit compared to windows. I would run turbostat while running the test to observe if excessive throttling occurs. And check for any temperature related messages in the log files (i.e. /var/log/kern.log, /var/log/syslog, dmesg, maybe "journalctl -e | grep -i temperature").

---

### Post by cedbarth on 2023-11-09
Hi,
As I see, you are having fun without me :-)
@Doug: Actually I still not have succeeded to set scaling driver to acpi-cpufreq, one of the ideas you had to solve my problem.
I have tried to boot with intel_pstate=disable argument, then scaling_driver is intel_cpufreq aka intel_pstate in passive mode .

I have also tried to echo off to /sys/devices/system/cpu/intel_pstate/status  as mentionned in this [post]("https://unix.stackexchange.com/questions/467505/change-the-cpufreq-driver-from-intel-pstate-to-acpi") but then /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver where not present anymore and I don't know what was then the scaling driver.

How do you set your scaling driver to acpi-cpufreq ?
Thanks for your help !
PS: Passmark is free on windows for 30 days

---

### Post by cedbarth on 2023-11-09
Using Chat GPT I've finally found the daemon that was erasing each try to set cpu scaling_governor to performance. Chat GPT gave me some advice and an obvious one was to check log messages and indeed as I was trying to set cpu scaling_governor to performance a daemon called tccd was resetting then the scaling_governor. I had tried before looking after laptop performance a software to tweak fan speed and tried to install  Tuxedo computer control center, and it was this daemon tccd that was messing up my scaling adjustments.
Well, once removed this daemon , I don't have anymore trouble setting cpus scaling_governors to performance but still the benchmark scores running linux are at 16000 instead of 20800 for windows.
When I run the test as root starting the test with sudo nice -n -20 ./pt_linux_x64 and run only the cpu test I get the same results more or less that I have already posted with difference in percentage with W11 results and the fan is unhearable, astoundingly quiet...

I have set /sys/devices/system/cpu/intel_pstate/hwp_dynamic_boost to 1, /sys/devices/system/cpu/intel_pstate/min_perf_pct to 100 and all /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor to performance.

Here is turbostat output:
```

root@kakak:/home/cedric# sudo turbostat --quiet --Summary --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 15
Busy%    Bzy_MHz    IRQ    PkgTmp    PkgWatt    CorWatt    GFXWatt    RAMWatt
0.63    1001    21451    56    5.21    2.16    0.00    0.00
0.65    1043    21507    56    5.18    2.16    0.00    0.00
79.76    3261    117029    74    31.77    28.60    0.00    0.00
89.74    1926    73125    77    17.92    12.52    0.00    0.00
95.25    1940    75463    81    18.66    14.06    0.00    0.00
63.52    1954    55714    72    13.85    10.38    0.00    0.00
87.20    1910    69199    85    18.98    14.09    0.00    0.00
17.41    1648    31664    70    7.42    4.06    0.00    0.00
0.59    954    20488    68    5.67    2.43    0.00    0.00


```

The 2 first and last lines where displayed before and after the test was run.
The max cpu frequency is 5 GHz and the fan is unhearable along the whole test !

and test results:

CPU Mark:                          16087
  Integer Math                     80816 Million Operations/s
  Floating Point Math              34555 Million Operations/s
  Prime Numbers                    72.5 Million Primes/s
  Sorting                          23270 Thousand Strings/s
  Encryption                       11174 MB/s
  Compression                      169027 KB/s
  CPU Single Threaded              1847 Million Operations/s
  Physics                          1684 Frames/s
  Extended Instructions (SSE)      8119 Million Matrices/s

Memory Mark:                       Incomplete
  Database Operations              0.0 Thousand Operations/s
  Memory Read Cached               0.0 MB/s
  Memory Read Uncached             0.0 MB/s
  Memory Write                     0.0 MB/s
  Available RAM                    0 Megabytes
  Memory Latency                   0 Nanoseconds
  Memory Threaded                  0.0 MB/s
--------------------------------------------------------------------------------

If I run the test with scaling_governor equal to powersave, then the result is around 13000 .

---

### Post by MAFoElffen on 2023-11-09
> **cedbarth said:**
> 
I have also tried to echo off to /sys/devices/system/cpu/intel_pstate/status  as mentioned in this [post]("https://unix.stackexchange.com/questions/467505/change-the-cpufreq-driver-from-intel-pstate-to-acpi") but then [COLOR=#ff0000]**/sys/devices/system/cpu/cpu*/cpufreq/scaling_driver **[/COLOR]where not present anymore and I don't know what was then the scaling driver.

How do you set your scaling driver to acpi-cpufreq ?

Wait... Doesn't intel_pstate use the acpi-cpufreq driver? Now I'm confused by that...

No. Will ot echo to it to change that. That's because that directory that is in, is the wrong place to do something like that... do "ls -lah" on it
```

$ ls -lah /sys/devices/system/cpu/cpu0/cpufreq/
total 0
drwxr-xr-x  2 root root    0 Nov  2 09:21 .
drwxr-xr-x 22 root root    0 Nov  2 09:21 ..
-r--r--r--  1 root root 4.0K Nov  8 17:05 affected_cpus
-r--r--r--  1 root root 4.0K Nov  8 17:05 base_frequency
-r--r--r--  1 root root 4.0K Nov  2 09:21 cpuinfo_max_freq
-r--r--r--  1 root root 4.0K Nov  2 09:21 cpuinfo_min_freq
-r--r--r--  1 root root 4.0K Nov  8 17:05 cpuinfo_transition_latency
-r--r--r--  1 root root 4.0K Nov  8 17:05 energy_performance_available_preferences
-rw-r--r--  1 root root 4.0K Nov  2 09:21 energy_performance_preference
-r--r--r--  1 root root 4.0K Nov  8 17:05 related_cpus
-r--r--r--  1 root root 4.0K Nov  8 17:05 scaling_available_governors
-r--r--r--  1 root root 4.0K Nov  8 17:05 scaling_cur_freq
[COLOR=#ff0000]-r--r--r--  1 root root 4.0K Nov  8 17:05 scaling_driver[/COLOR]
-rw-r--r--  1 root root 4.0K Nov  8 17:05 scaling_governor
-rw-r--r--  1 root root 4.0K Nov  8 17:05 scaling_max_freq
-rw-r--r--  1 root root 4.0K Nov  8 17:05 scaling_min_freq
-rw-r--r--  1 root root 4.0K Nov  8 17:05 scaling_setspeed

```
That is read-only there

Wait on Doug S 

@Doug S -- Just to Doug... He will know what this means. (Just a bug in his ear to see what he thinks.)

He has 13th Gen... what about "intel_pstate=no_hwp" <-- That is what is used fro overclockig... But then there is this, that if hwp, is supposed to be how it works:
> 
 **HWP + performance**

 In this configuration intel_pstate will write 0 to the processor&#8217;s Energy-Performance Preference (EPP) knob (if supported) or its Energy-Performance Bias (EPB) knob (otherwise), which means that the processor&#8217;s internal P-state selection logic is expected to focus entirely on performance.

 This will override the EPP/EPB setting coming from the sysfs interface (see [Energy vs Performance Hints]("https://www.kernel.org/doc/html/v5.0/admin-guide/pm/intel_pstate.html#energy-vs-performance-hints") below).

 Also, in this configuration the range of P-states available to the processor&#8217;s internal P-state selection logic is always restricted to the upper boundary (that is, the maximum P-state that the driver is allowed to use).

 

But then, if that is not what you want... What about 
```

modprobe p4-clockmod

```
Then persistent as 
```

# File /etc/modprobe.d/scaling_driver.conf
#
blacklist acpi-cpufreq
# where it is located
options p4-clockmod

```
Or with Grub parameters:
```

intel_idle.max_cstate=0 intel_pstate=disable p4-clockmod

```
Just throwing out ideas...

---

### Post by Doug S on 2023-11-10
Hi All,

Watch for edits to this post. It is going to take me awhile to address everything.

I assume "tccd" means "TUXEDO Control Center". I had never heard of it. I am a server person and would never use such a utility.

With all that we have now learned, it needs to be stated (again) that your results are independent of CPU frequency scaling driver and governor. Why? Because the CPUs go flat out anyhow.

From your turbostat output it looks as though your laptop is thermal limit throttling. For example, the 85 degrees line at 1.9 GHz. Notice how the CPU goes up to 3.26 GHz and then throttles back to 1.9 GHz. The sampling interval of 15 seconds is too long for this case. Try 1 second to gain better insight into the actions. OR run the test for much longer. I used "./pt_linux_x64 -i 5 -d 3 -r 1" for my longer run example, with turbostat sampling at 5 seconds per.

Are you able to determine what is your current processor temperature limit before Thermal throttling? Is it set via the tccd app? It looks like somewhere in around 75 degrees (and under-damped, giving large oscillations), which is reasonable. I use 75 degrees. From [another thread I was trying to help with]("https://askubuntu.com/questions/1490742/why-does-ubuntu-throttle-my-cpu-9-sooner-than-what-crit-says"), the poster said when they booted with windows the processor was allowed to go to 98 degrees C. Myself, I wouldn't allow it.

EDITS:

I missed that you have disabled tccd already.

> **cedbarth said:**
> How do you set your scaling driver to acpi-cpufreq ?
 I use the grub command line method. For your case it might be that the intel_pstate driver is forced for some reason, perhaps HWP can not be disabled. Some BIOSs do not allow HWP to be an OS decision. You should be able to find related messages in dmesg. Example:
```
doug@s19:~/passmark/PerformanceTest$ sudo dmesg | grep -i intel_pstate
[    0.371000] intel_pstate: Intel P-state driver initializing
[    0.371620] intel_pstate: HWP enabled
```

> **cedbarth said:**
> If I run the test with scaling_governor equal to powersave, then the result is around 13000 .O.K. that is very interesting and not what both MAFoElffen and I got. I'll have to think more, but I am wondering if idle_injection is being used as one of the thermal throttle methods.

> **MAFoElffen said:**
> Wait... Doesn't intel_pstate use the acpi-cpufreq driver? Now I'm confused by that...No, the intel_pstate CPU frequency driver is entirely different than the acpi-cpufreq CPU frequency scaling driver. I have never heard of being able to switch between the 2 on the fly. I'll play with that later.

> **MAFoElffen said:**
> He has 13th Gen... what about "intel_pstate=no_hwp" I think that was tried earlier. It can be difficult to know if HWP is on or not, and sometimes it is forced by a BIOS setting. I have a program that tells me if HWP is enabled or not.

> **MAFoElffen said:**
> What about 
```

modprobe p4-clockmod

```
I have never heard of p4-clockmod. I will have to do some studying in the background, but at low priority.

> **cedbarth said:**
> PS: Passmark is free on windows for 30 daysO.K., but my test server is not dual boot. I think my previous link where one can compare my test server results with 10 other windows computers with the same processor was a good enough compare.

At this point, and with all that we have learned, I think the root difference is thermal throttling. Perhaps one or both of different trips points and different methods of implementation.
For example I once [compared idle_injection verses CPU maximum frequency reduction methods]("https://askubuntu.com/questions/1153613/ubuntu-19-kidle-inject-process/1153772#1153772") of thermal throttling and found a between 28% to 33% performance difference between them. (That was years ago, and I do not know if it still stands).

---

### Post by MAFoElffen on 2023-11-10
Yup. Thermal throttling would account for a lot of difference if comparing 75 and 95. Someone would have to set both at the same, then test to see if there was a difference between. 

I do have dual-boot on my workstation (Win11 & Ubuntu 22.04.3), but... The only time I see it stressed with it's i9 is when I have a bunch of VM's up working hard with automated tests, then do some compiles. I would have to artificially stress it, and I only have it air-cooled with 12 fans...

Right now, I'm not trying to make many changes to it because I have an open support case open with the Intel Support Engineers on their upstream Linux Drivers (intel-i915-dkms)... That has been a pain.

Once that is done, then I will try out '[corectrl]("https://launchpad.net/~ernstp/+archive/ubuntu/mesarc")' on it... it's in the Lunar, and newer repo's

---

### Post by Doug S on 2023-11-10
It looks as though your system is severely thermal throttling. Perhaps both CPU frequency reduction and idle injection or clock modulation. 
What do you get for:

```
sudo systemctl status thermald
```

If you see that it is enabled and active and using the "--adaptive" option then note that I am not up to date with [the DPTF stuff]("https://docs.kernel.org/driver-api/thermal/intel_dptf.html").

I use the TCC offset method for thermal limiting and always have thermald disabled. The TCC offset method has a limit only being able to reduce the CPU frequency to the non-turbo limit, and currently your system needs more than that.

---

### Post by Doug S on 2023-11-10
> **cedbarth said:**
> I have also tried to echo off to /sys/devices/system/cpu/intel_pstate/status  as mentionned in this [post]("https://unix.stackexchange.com/questions/467505/change-the-cpufreq-driver-from-intel-pstate-to-acpi") but then /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver where not present anymore and I don't know what was then the scaling driver.

I get the same, and can only do it with HWP disabled:

```
doug@s19:~$ ls -l /sys/devices/system/cpu/intel_pstate/status
-rw-r--r-- 1 root root 4096 Nov 10 08:54 /sys/devices/system/cpu/intel_pstate/status
doug@s19:~$ cat /sys/devices/system/cpu/intel_pstate/status
off
```And there doesn't seem to be any driver at all active. I set it back to active.

---

### Post by MAFoElffen on 2023-11-10
That struck a note, and then I remembered...
> **cedbarth said:**
> Hi,
I have a pcspecialist _laptop_ with [COLOR=#ff0000]i7-1360P[/COLOR] 32 Gb ram and 2Tb 990 pro nvm ssd
From the first sentence of Post #1...
RE: [https://ark.intel.com/content/www/us/en/ark/products/232155/intel-core-i7-1360p-processor-18m-cache-up-to-5-00-ghz.html](https://ark.intel.com/content/www/us/en/ark/products/232155/intel-core-i7-1360p-processor-18m-cache-up-to-5-00-ghz.html)

There is only so much you are going to be able to do with keeping that "Mobile" chip cool, even with the thermal monitoring limits built into that. And the BIOS probably has some more ACPI limits to that, just because it is a laptop. When it reaches whatever limit you set it to, then it will lower itself to protect itself from the heat.

Look at me(?) I have 12 fans on my workstation. Doug's is water cooled... 

I have a 2 fan cooler pad that I use my Lenovo laptop (i7) on... I take it apart and blow it out occasionally... *and* I still worry about the heat buildup on it. I'll play on my server and workstation (both i9's), because I've built them for heavy use. Laptop's have soldered-in CPU's and very limited heat sinks and fans. I don't play with the CPU Freq's on my laptop.

---

### Post by cedbarth on 2023-11-10
Hi all,
Thanks for your help

@Doug: You got it, there is a very quick thermal throttling as you can see below for the first period of the test run:
```

root@kakak:/home/cedric# turbostat --quiet --Summary --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 1
Busy%    Bzy_MHz    IRQ    PkgTmp    PkgWatt    CorWatt    GFXWatt    RAMWatt
1.32    1598    1920    60    6.12    2.34    0.00    0.00
1.35    1355    1951    60    5.98    2.16    0.00    0.00
1.51    1914    2250    59    6.61    2.75    0.01    0.00
1.13    1298    1726    59    5.56    1.92    0.00    0.00
35.07    3622    4262    92    22.15    18.53    0.00    0.00
99.75    3521    10903    92    44.43    41.21    0.00    0.00
99.77    3603    10832    92    42.34    39.05    0.00    0.00
99.77    3548    10560    92    40.85    37.45    0.00    0.00
99.77    3496    11325    92    39.23    35.96    0.00    0.00
99.77    3453    11112    92    38.33    35.01    0.00    0.00
99.77    3409    11076    92    37.03    33.74    0.00    0.00
99.41    3306    10960    91    36.33    32.94    0.00    0.00
99.75    3124    10044    90    34.95    31.58    0.00    0.00
99.77    2103    5335    75    16.30    12.91    0.00    0.00
99.77    1950    5352    75    14.58    11.18    0.00    0.00
96.61    1958    5334    75    14.53    10.99    0.00    0.00
96.36    1959    5967    75    14.70    11.07    0.00    0.00
99.77    1950    5344    75    14.60    11.24    0.00    0.00
99.37    1950    5358    76    14.80    11.42    0.00    0.00
99.77    1945    5479    76    15.52    12.16    0.00    0.00
98.13    1954    5396    75    19.09    12.60    0.00    0.00
94.50    1963    5134    75    19.32    12.59    0.00    0.00
99.77    1950    5280    75    19.69    12.91    0.00    0.00
99.77    1950    5326    75    19.70    12.90    0.00    0.00
99.77    1950    5232    75    19.68    12.92    0.00    0.00
99.29    1951    5537    76    19.69    12.90    0.00    0.00
76.50    1897    5096    76    16.05    11.85    0.00    0.00
76.37    1870    4884    76    17.75    12.76    0.00    0.00

```

The big bug actually is the fan control in linux for this laptop , I almost don't hear the fan whereas it should be running more or less at fullspeed the way it does during the same test on windows 11.
It seems linux doesn't control at all the fan.
I had noticed than if I run windows and use some third party software to tweak the fan curve so that below 70°C, the fan speed is 22% , almost unhearable, then if I reboot and run linux, I don't hear it neither, I presume the same fan speed is left.
If I use under windows the same 3rd party fan software to set fan speed to 50% ( around 4000 rpm) quite noisy and then restart the laptop under ubuntu, then the fan is hearable but lower than fan noise at 50% as in windows. It seems then that linux lowers fan speed at startup, but clearly hearable.
 If I could at least toggle the fan to its full speed and switch it back to a lower value afterwards, it would be merely solve this issue

---

### Post by MAFoElffen on 2023-11-10
Have you tried this on your laptop to see if it works with your hardware?
[https://snapcraft.io/pi-fancontrol](https://snapcraft.io/pi-fancontrol)

Then this one works with lm-sensors: [https://packages.ubuntu.com/jammy/fancontrol](https://packages.ubuntu.com/jammy/fancontrol)
^^^ How to set that up: [https://askubuntu.com/a/46135/138255](https://askubuntu.com/a/46135/138255)

---

### Post by cedbarth on 2023-11-10
pi-fancontrol is for raspberry-pi and it's said it works only for ARM images, I guess it won't work with my Intel laptop.

Well , now it's clear that the previous windows fan speed stays the same when I reboot in linux. I've just tested to reboot linux after setting full fan speed in windows 11 and I get full fan speed continuously in linux.
It also mean that I have a very slow way to switch from no fan noise to full fan speed , hibernating linux, booting windows and setting full fan speed and resuming hibernation from linux.Actually, even if thermal throttling seems quite or even too effective in linux, I would feel more secure if I could have a cpu temperature indicator in the gnome top bar and a popup window that could warn me if cpu temperature gets too hot , as there is stricltly no fan control up to now.
I get the same benchmark results with full fan speed :-( as the system throtttles quickly and doesn't enable the cpu freq to rise up again after 92°C is reached, then cpu frequency is around 2 Ghz in performance mode and temperature is a bit lower at full fan speed around 62°C .
Here is partial turbostat output:

```

0.25    1886    191    46    3.01    0.27    0.00    0.00
0.17    2352    165    45    2.81    0.24    0.00    0.00
71.28    3913    2958    90    46.21    43.35    0.00    0.00
99.70    3929    4486    90    57.91    54.96    0.00    0.00
99.77    3950    4113    91    55.87    52.91    0.00    0.00
99.77    3941    8346    92    55.91    52.92    0.00    0.00
99.77    3901    9791    91    54.08    51.03    0.00    0.00
99.77    3857    9470    90    51.97    48.89    0.00    0.00
99.77    3825    9645    91    50.63    47.48    0.00    0.00
99.07    2435    4913    65    21.58    18.50    0.00    0.00
95.76    1958    4154    63    13.97    10.97    0.00    0.00
96.08    1967    4026    63    13.61    10.58    0.00    0.00
99.77    2000    4126    62    14.09    11.08    0.00    0.00
99.77    2014    4052    62    14.40    11.23    0.00    0.00
99.77    2025    4042    62    14.33    11.33    0.00    0.00
99.77    2039    4136    62    14.49    11.49    0.00    0.00
98.41    2009    4172    62    14.79    11.77    0.00    0.00
98.90    1945    4185    62    17.14    12.29    0.00    0.00
93.63    1934    4297    61    18.92    12.64    0.00    0.00
98.87    1948    4111    62    19.00    12.59    0.00    0.00
99.77    1950    4091    62    19.05    12.65    0.00    0.00
99.77    1950    4124    61    19.04    12.61    0.00    0.00
99.77    1950    4068    62    19.05    12.61    0.00    0.00
81.43    1929    3987    62    16.45    11.47    0.00    0.00
74.98    1864    3588    61    15.35    11.75    0.00    0.00
75.02    1867    3606    61    18.49    12.96    0.00    0.00
75.00    1867    3582    62    18.42    12.99    0.00    0.00

```

I would be cool to be able to tweak this thermal throttling algorithm.
Seems when 92°C cpu temperature is hit, the cpu is doomed to work at 2000 MHz for ages even though the temperature has well cooled down below 92°C ...

---

### Post by MAFoElffen on 2023-11-10
I don't have a Gnome Indicator, but I do use lm-sensors with my own tweaked 'conky' script so i can keep track of things going on.

Dang. I am not on that machine at the moment. I used to have a screen shot of that in my uploads. I'm missing some albums and the uploads only go back so far now(?) Dang.

Here is an example (attached)

Dang, I found a Gnome extension for the top bar! "[Freon]("https://extensions.gnome.org/extension/841/freon/")"

---

### Post by Doug S on 2023-11-10
Thanks for all the updates. I am not knowledgeable about fan control with linux, and can not help. I use Asus motherboards and fan control is via the BIOS. I have my fan curve set just the way I like it, but all in BIOS.

Your thermal trip point does seem somewhat sticky. I don't know if that is some very long time constant or what?

I have been playing around with thermald, trying to remember what the various cooling modes actually do. The "Processor" cooling device is extremely coarse and slow.My notes, README.txt, file:

```
doug@s19:~/config/etc/thermald$ cat README.txt
2023.11.10: Since I can never remember:

Note: It clobbers my TCC offset on startup and sets it to 5 degrees. It also messes with it on the fly. Grrr... How stupid is that?
Note: For some test, I don't which know one but I suspect rapl_controller, is disabled PKG Limit #2. Oh my god!!! Grrrr...

rapl_controller is to throttle via adjusting power limits.

intel_pstate is to throttle via max CPU frequency limits via /sys/devices/system/cpu/intel_pstate/max_perf_pct and via turbo enable/disable.

intel_powerclamp is to throttle via idle_inject.

cpufreq does not do anything when using the intel_pstate or intel_cpufreq drivers.

Processor is to throttle via max CPU frequency limits via sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq.
It does adjust via, for example:
/sys/devices/virtual/thermal/cooling_device10/cur_state (all of the ones with type "Processor").
It is very very coarse, with only 3 adjustment states.
It is implemented via drivers/acpi/processor_thermal.c

Conclusion: I have never liked Thermald, and now I remember why.
```

Myself, I prefer a very simple thermal control method. If I ever have to use Thermald, I use the simplist control file and only one entry in the thermal-cpu-cdev-order.xml file. I can help with that if you want. But, I agree you need to get your fans working properly.

EDIT: For the i7-1360P processor the Passmark CPU Mark median score is 19,855 and the average is 19,244.

---

### Post by Doug S on 2023-11-18
I would be very interested in an update on this one. Any progress?

---

