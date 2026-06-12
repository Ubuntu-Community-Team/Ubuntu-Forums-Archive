---
title: "Processor Problems?"
date: 2012-11-14
forum: General Help
---

### Post by awgord on 2012-11-14
Hello everyone,

I'm very new to the community, and also very new to using Ubuntu / Linux.  I have a question that I've been searching and searching for a few days for the answer, and I'm afraid I just can't find anything helpful.

I'll admit now that I'm not much of a coder / programmer at all, I am just bored and wanting to try something different out.  I've heard for years about Linux, and found Ubuntu Studio and thought it seemed interesting and wanted to try it out.

Now, the problem I'm having is this:  For some reason the Ubuntu Studio OS does NOT see more than one core for my processor.  I've installed and tried version 12.10, and since that one didn't work I figured the LTS 12.04 version might, but same thing.

My BIOS is set to ACPI Enabled, my processor is an AMD Phenom 8400 Triple-Core.

I'm running the 64bit version of the OS, as I figured it should be okay since my Win7 is 64 bit.

Is there anything that anyone can suggest, hopefully that doesn't go too over my head.

Thank you very much for the responses, and allow me to apologize if this has been answered before - I can't seem to find any threads that had any helpful info for me.

---

### Post by jerome1232 on 2012-11-14
How is it you came to arrive at the conclusion that Ubuntu is only seeing one core?

What does this show?
```

grep cores /proc/cpuinfo 
```

---

### Post by awgord on 2012-11-14
> **jerome1232 said:**
> How is it you came to arrive at the conclusion that Ubuntu is only seeing one core?

What does this show?
```

grep cores /proc/cpuinfo 
```


When I used cat /proc/cpuinfo it would only show details for processor 0, no other details.

The answer to your question is:  cpu cores :1

---

### Post by Doug S on 2012-11-14
I looked around some, and there seems to have been other occurances of the same issue, although they also claim to be solved.
 
Suggest that you have a close look at /var/log/kern.log for entries during start up. Try to find the area where it detects core 0 and tries to proceed from there. Look for any complaint or error type entries. Also look to see that the CPU is correctly identified.
 
Here is an example from one of my computers (yours has a different CPU and will differ):```
Nov 13 17:24:12 s15 kernel: [    0.002201] CPU: Physical Processor ID: 0
Nov 13 17:24:12 s15 kernel: [    0.002203] CPU: Processor [COLOR=red]Core ID: 0[/COLOR]
Nov 13 17:24:12 s15 kernel: [    0.002207] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Nov 13 17:24:12 s15 kernel: [    0.002208] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Nov 13 17:24:12 s15 kernel: [    0.002212] mce: CPU supports 9 MCE banks
Nov 13 17:24:12 s15 kernel: [    0.002223] CPU0: Thermal monitoring enabled (TM1)
Nov 13 17:24:12 s15 kernel: [    0.002229] using mwait in idle threads.
Nov 13 17:24:12 s15 kernel: [    0.003966] ACPI: Core revision 20110623
Nov 13 17:24:12 s15 kernel: [    0.013929] ftrace: allocating 27014 entries in 106 pages
Nov 13 17:24:12 s15 kernel: [    0.021241] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 13 17:24:12 s15 kernel: [    0.060900] [COLOR=red]CPU0: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz stepping 07[/COLOR]
Nov 13 17:24:12 s15 kernel: [    0.164903] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
Nov 13 17:24:12 s15 kernel: [    0.164908] PEBS disabled due to CPU errata.
Nov 13 17:24:12 s15 kernel: [    0.164910] ... version:                3
Nov 13 17:24:12 s15 kernel: [    0.164912] ... bit width:              48
Nov 13 17:24:12 s15 kernel: [    0.164913] ... generic registers:      4
Nov 13 17:24:12 s15 kernel: [    0.164915] ... value mask:             0000ffffffffffff
Nov 13 17:24:12 s15 kernel: [    0.164917] ... max period:             000000007fffffff
Nov 13 17:24:12 s15 kernel: [    0.164918] ... fixed-purpose events:   3
Nov 13 17:24:12 s15 kernel: [    0.164920] ... event mask:             000000070000000f
Nov 13 17:24:12 s15 kernel: [    0.165024] NMI watchdog enabled, takes one hw-pmu counter.
Nov 13 17:24:12 s15 kernel: [    0.165073] Booting Node   0, Processors  #1
Nov 13 17:24:12 s15 kernel: [    0.165075] smpboot cpu 1: start_ip = 98000
Nov 13 17:24:12 s15 kernel: [    0.272931] NMI watchdog enabled, takes one hw-pmu counter.
Nov 13 17:24:12 s15 kernel: [    0.272995]  #2
Nov 13 17:24:12 s15 kernel: [    0.272996] smpboot cpu 2: start_ip = 98000
Nov 13 17:24:12 s15 kernel: [    0.380847] NMI watchdog enabled, takes one hw-pmu counter.
Nov 13 17:24:12 s15 kernel: [    0.380908]  #3
Nov 13 17:24:12 s15 kernel: [    0.380909] smpboot cpu 3: start_ip = 98000
Nov 13 17:24:12 s15 kernel: [    0.488759] NMI watchdog enabled, takes one hw-pmu counter.
Nov 13 17:24:12 s15 kernel: [    0.488819]  #4
Nov 13 17:24:12 s15 kernel: [    0.488821] smpboot cpu 4: start_ip = 98000
Nov 13 17:24:12 s15 kernel: [    0.596673] NMI watchdog enabled, takes one hw-pmu counter.
Nov 13 17:24:12 s15 kernel: [    0.596742]  #5
Nov 13 17:24:12 s15 kernel: [    0.596744] smpboot cpu 5: start_ip = 98000
Nov 13 17:24:12 s15 kernel: [    0.704597] NMI watchdog enabled, takes one hw-pmu counter.
Nov 13 17:24:12 s15 kernel: [    0.704659]  #6
Nov 13 17:24:12 s15 kernel: [    0.704660] smpboot cpu 6: start_ip = 98000
Nov 13 17:24:12 s15 kernel: [    0.812611] NMI watchdog enabled, takes one hw-pmu counter.
Nov 13 17:24:12 s15 kernel: [    0.812672]  #7 Ok.
Nov 13 17:24:12 s15 kernel: [    0.812674] smpboot cpu 7: start_ip = 98000
Nov 13 17:24:12 s15 kernel: [    0.920525] NMI watchdog enabled, takes one hw-pmu counter.
Nov 13 17:24:12 s15 kernel: [    0.920550] [COLOR=red]Brought up 8 CPUs[/COLOR]
Nov 13 17:24:12 s15 kernel: [    0.920552] Total of 8 processors activated (54576.62 BogoMIPS).
```

---

### Post by awgord on 2012-11-14
Thanks for the reply Doug!

I checked out what you said, and it spit back a bunch of info, so much that I couldn't scroll all the way to the top of it, and in the part that I could read, there was nothing saying anything about the cpus.

Not that it would matter if it did anyway, as something like that I'm not too sure how to fix.

I guess I was kind of hoping that someone would know of a "click this and it will fix it" or "type this and it will fix it" solution.

I'm not sure if this helps at all, but here is the read out from my /proc/cpuinfo

cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 8400 Triple-Core Processor
stepping	: 2
microcode	: 0x1000065
cpu MHz		: 1050.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips	: 4199.98
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by Doug S on 2012-11-14
I assumed you would use an editor to look at the file. I like "nano" and pretty much use only it on linux. You could also "cat /var/log/kern.log | more" to get a screen full at a time.
Your computer seems to identify the CPU properly, so the question is what happens when it tries to start the other cores? There should be some entries in the kern.log file that might help us understand.

---

### Post by awgord on 2012-11-14
Thanks again Doug, after using the | more command, I was able to slowly go through line by line.

Of course, as mentioned before my ability to read programming code & understand how to fix it is....  well weak would be an understatement.....  anyway, I went through and this is what I found about the processors; it says that CPU 1 & 2 are not responding.




Ubuntu kernel: [    0.003806] tseg: 00bff00000
Ubuntu kernel: [    0.003808] CPU: Physical Processor ID: 0
Ubuntu kernel: [    0.003809] CPU: Processor Core ID: 0
Ubuntu kernel: [    0.003811] mce: CPU supports 6 MCE banks
Ubuntu kernel: [    0.003818] LVT offset 0 assigned for vector 0xf9
Ubuntu kernel: [    0.003823] using AMD E400 aware idle routine
Ubuntu kernel: [    0.004623] ACPI: Core revision 20120320
Ubuntu kernel: [    0.012173] ftrace: allocating 25103 entries in 99 pages
Ubuntu kernel: [    0.250576] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Ubuntu kernel: [    0.260569] CPU0: AMD Phenom(tm) 8400 Triple-Core Processor stepping 02
Ubuntu kernel: [    0.361581] Performance Events: AMD PMU driver.
Ubuntu kernel: [    0.361585] ... version:                0
Ubuntu kernel: [    0.361587] ... bit width:              48
Ubuntu kernel: [    0.361588] ... generic registers:      4
Ubuntu kernel: [    0.361589] ... value mask:             0000ffffffffffff
Ubuntu kernel: [    0.361591] ... max period:             00007fffffffffff
Ubuntu kernel: [    0.361592] ... fixed-purpose events:   0
Ubuntu kernel: [    0.361593] ... event mask:             000000000000000f
Ubuntu kernel: [    0.367641] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Ubuntu kernel: [    0.371577] Booting Node   0, Processors  #1
Ubuntu kernel: [    5.930942] CPU1: Not responding.
Ubuntu kernel: [    5.934421]  #2
Ubuntu kernel: [   11.494059] CPU2: Not responding.
Ubuntu kernel: [   11.494104] Brought up 1 CPUs
Ubuntu kernel: [   11.494106] Total of 1 processors activated (4199.98 BogoMIPS).
Ubuntu kernel: [   11.495591] devtmpfs: initialized

---

### Post by awgord on 2012-11-15
I should add that since 12.04 was not recognizing all the cores I went and reinstalled version 12.10 again.

Does anyone have any ideas or suggestions?

---

### Post by cwsnyder on 2012-11-15
Are you sure that Windows is seeing all of your processor cores?  Windows may have 'parked' some of the processor cores to reduce power consumption. Check out this video on Youtube: [http://www.youtube.com/watch?v=pl3u9eiskM4](http://www.youtube.com/watch?v=pl3u9eiskM4)

You might also check out your GRUB startup by restarting, moving to your normal OS choice and pressing the E key to edit your GRUB startup and make sure you don't have something set like **maxcpus=1**.

---

### Post by Doug S on 2012-11-15
Hmmm... The kern.log segment only confirms what we already know and doesn't provide more insight.
 
I spent time last night searching around about your issue, but didn't find much.
Are you sure all cores are enabled in the BIOS?
 
I don't understand the comment about windows "parking" (I watched the video), as that is a completely different operating system and a windows registry setting would not carry over.

---

### Post by awgord on 2012-11-15
@cwsnyder

I was pretty sure that Windows was using all cores as the "Performance" tab of Task Manager shows 3 live graphs for CPU Usage History, and watching the CPU Usage bar graph in Windows while going through start up, it rarely goes over 50% for very long as compared to watching the system monitor in Ubuntu Studio and doing anything from opening a web page to minimizing it causes the lone orange CPU monitor to top out at 100%.

Still though, I watched your video and went through the registry to change the values that were mentioned in there.  

During the reboot, I looked at the GRUB editor and did not see anything that said maxcpu=1.

I'm back in Windows right now, and it seems to run a bit faster thanks to your suggestion for the registry edit.  I'm about to log out and back in to Ubuntu to see if that made a difference.



@Doug

I don't see anything in my BIOS regarding CPU cores, the only thing I see is "Enable ACPI" which is enabled.  Now, again, I'm not sure if that pertains to CPU's or not, I'm just going by what I read in regards to trying to find an answer before coming to the forums, and that was a suggestion that someone had made to someone else.


I thank you both for your help in trying to remedy this problem, and will now boot up in to Ubuntu to see if CW's solution had an effect in Ubuntu.



***UPDATE***:  Nothing has changed

---

### Post by Doug S on 2012-11-15
I did not realize that your computer was dual boot, and it is easy for you to do back to windows. Obviously if the thress cores are being used by windows, then they are not disabled in BIOS. 
When you were searching around did you notice some references to USB hubs and problems? Do you have a USB hub and if yes, can you try to remove it? Otherwise I am out of ideas, except to maybe try version 10.04.

---

### Post by cwsnyder on 2012-11-15
One last try from [http://www.cyberciti.biz/faq/debian-rhel-centos-redhat-suse-hotplug-cpu/](http://www.cyberciti.biz/faq/debian-rhel-centos-redhat-suse-hotplug-cpu/)  and [http://www.upubuntu.com/2011/09/how-to-disable-cpu-core-on-ubuntudebian.html](http://www.upubuntu.com/2011/09/how-to-disable-cpu-core-on-ubuntudebian.html) : open a terminal and enter the following ```
cd /sys/devices/system/cpu
ls -l
``` (that is the lower case L)  The listing should match something like ```
cws@debian:/sys/devices/system/cpu$ ls -l
total 0
drwxr-xr-x 6 root root    0 Nov 15 13:13 cpu0
drwxr-xr-x 6 root root    0 Nov 15 15:02 cpu1
drwxr-xr-x 6 root root    0 Nov 15 15:02 cpu2
drwxr-xr-x 3 root root    0 Nov 15 15:02 cpufreq
drwxr-xr-x 2 root root    0 Nov 15 15:02 cpuidle
-r--r--r-- 1 root root 4096 Nov 15 15:02 kernel_max
-r--r--r-- 1 root root 4096 Nov 15 15:02 modalias
-r--r--r-- 1 root root 4096 Nov 15 15:02 offline
-r--r--r-- 1 root root 4096 Nov 15 15:02 online
-r--r--r-- 1 root root 4096 Nov 15 15:02 possible
drwxr-xr-x 2 root root    0 Nov 15 15:02 power
-r--r--r-- 1 root root 4096 Nov 15 15:02 present
--w------- 1 root root 4096 Nov 15 15:02 probe
--w------- 1 root root 4096 Nov 15 15:02 release
-rw-r--r-- 1 root root 4096 Nov 15 13:09 sched_mc_power_savings
-rw-r--r-- 1 root root 4096 Nov 15 15:02 uevent
cws@debian:/sys/devices/system/cpu$ 
```To turn on cpu1 or cpu2, you write a 1 to their corresponding **online** subdirectory, as for example:```
cws@debian:/sys/devices/system/cpu$ echo 1 | sudo tee /sys/devices/system/cpu/cpu1/online
cws@debian:/sys/devices/system/cpu$ sudo grep "processor" /proc/cpuinfo
```

---

### Post by Doug S on 2012-11-15
Ya, I saw that, or similair, last night. In the example I saw there was no listing for cpu1 and cpu2 when they were not detected at startup.
 
But please try it and let us know what you get on your system.

---

### Post by awgord on 2012-11-15
Okay, so I did as you suggested CW and this is what I got:

```
andy@Andy-PC-Ubuntu:~$ cd /sys/devices/system/cpu
andy@Andy-PC-Ubuntu:/sys/devices/system/cpu$ ls -l
total 0
drwxr-xr-x 7 root root    0 Nov 15 09:32 cpu0
drwxr-xr-x 3 root root    0 Nov 15 15:33 cpufreq
drwxr-xr-x 2 root root    0 Nov 15 15:33 cpuidle
-r--r--r-- 1 root root 4096 Nov 15 15:37 kernel_max
-r--r--r-- 1 root root 4096 Nov 15 15:37 modalias
-r--r--r-- 1 root root 4096 Nov 15 15:37 offline
-r--r--r-- 1 root root 4096 Nov 15 15:32 online
-r--r--r-- 1 root root 4096 Nov 15 15:37 possible
drwxr-xr-x 2 root root    0 Nov 15 15:37 power
-r--r--r-- 1 root root 4096 Nov 15 15:37 present
--w------- 1 root root 4096 Nov 15 15:37 probe
--w------- 1 root root 4096 Nov 15 15:37 release
-rw-r--r-- 1 root root 4096 Nov 15 15:32 uevent
andy@Andy-PC-Ubuntu:/sys/devices/system/cpu$ 
```


However, when I tried to run the next command, this was the result:


```
andy@Andy-PC-Ubuntu:/sys/devices/system/cpu$ echo 1 | sudo tee /sys/devices/system/cpu/cpu1/online
tee: /sys/devices/system/cpu/cpu1/online: No such file or directory
1
andy@Andy-PC-Ubuntu:/sys/devices/system/cpu$ 
```



I thought maybe something was wrong with the install, so I tried running the OS right off the disc (Try before Installing) but, no, it still only sees one core. 

As for a USB hub, my keyboard has 2 extra USB ports, one of which I use for my mouse, but that is all for a hub that I have.  Not sure if that would be a problem, but hell, I'll try anything - although I hope it's not the keyboard, as my back up is..... not as nice lol


I'll let you know how it goes, thanks guys.

---

### Post by awgord on 2012-11-15
> **Doug S said:**
> I did not realize that your computer was dual boot, and it is easy for you to do back to windows. Obviously if the thress cores are being used by windows, then they are not disabled in BIOS. 
When you were searching around did you notice some references to USB hubs and problems? Do you have a USB hub and if yes, can you try to remove it? Otherwise I am out of ideas, except to maybe try version 10.04.



And THERE you have it.....  the problem was indeed a USB hub - unhooked my Logitech G15 keyboard and plugged in an older keyboard with no extra USB ports, reboot, and there we have it - all 3 processors are now being used...


```
andy@Andy-PC-Ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 8400 Triple-Core Processor
stepping	: 2
microcode	: 0x1000065
cpu MHz		: 1050.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 0
cpu cores	: 3
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips	: 4199.82
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 8400 Triple-Core Processor
stepping	: 2
microcode	: 0x1000065
cpu MHz		: 1050.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 1
cpu cores	: 3
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips	: 4199.82
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 8400 Triple-Core Processor
stepping	: 2
microcode	: 0x1000065
cpu MHz		: 1050.000
cache size	: 512 KB
physical id	: 0
siblings	: 3
core id		: 2
cpu cores	: 3
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock
bogomips	: 4199.82
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```


Thank you so much Doug, and you too CW, I really appreciate the help!

Now to find a fix to use my G15...  off I go! 

Thanks again!

---

### Post by Doug S on 2012-11-15
Glad you got it figured out, and thanks so much for reporting back. Very often we never hear back if the issue got solved or how.
 
By the way, I think this one was more advanced than typical first postings. Well done in sticking with it to the end.

---

### Post by awgord on 2012-11-15
Thanks again Doug, really though, I don't think I would have thought of the keyboard (USB hub) thing as in all the searching I did, I really can't recall seeing anything mentioned about problems with USB hubs.

Seems rather silly when you think about it, or at least it does for me when I think about it, that for some reason a keyboard with 2 extra USB hubs would cause 2 cores of your processor to not be usable.

Oh well, I'm sure I'll be able to find a fix for that and will have my G15 up and running again!  If not, well, I've been kind of wanting a new keyboard for a while now anyway :P

---

