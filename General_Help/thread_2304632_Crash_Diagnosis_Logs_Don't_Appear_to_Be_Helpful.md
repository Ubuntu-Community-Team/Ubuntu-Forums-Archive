---
title: "Crash Diagnosis: Logs Don't Appear to Be Helpful"
date: 2015-11-28
forum: General Help
---

### Post by SlidingHorn on 2015-11-28
I'll try to make this as quick as possible:  I have a new HP 15, on which I installed Xubuntu.  I promptly removed all xfce-and-GUI related items, then reinstalled X, installed xdm & openbox

```
sudo apt-get purge xconf xfwm4 xfce4-session thunar xfdesktop4 exo-utils xfce4-panel xfce4-terminal libxfce4util-common libxfce4ui-common xfce4-power-manager-data xfce4-taskmanager sfpanel-switch xfdesktop4-data light-locker lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings xubuntu-default-settings liblightdm-gobject-1-0 plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text xubuntu-artwork xubuntu-community-wallpapers xubuntu-docs xubuntu-icon-theme xubuntu-wallpapers

sudo apt-get autoremove

sudo apt-get install xdm openbox
```

Everything appears to have gone smoothly, until I ran into a random crash issue when using "high" resource applications (e.g. running video for extended periods of time in chromium, trying to play Regnum).  I've attempted to diagnose the issue by following [https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash), so I logged in from my tower via SSH and watched /proc/kmsg, /var/log/syslog, and /var/log/dmesg.  Unfortunately, there was nothing related in the logs, and post-crash, the system is unresponsive via SSH (which leads me to believe it's not X that's crashed).

Anyone have any ideas on how I could further look into this?

Some possibly useful info:

```
$lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)


$sudo lshw -C video
*- display
   description: VGA compatible controller
   protuct: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 0e
   width 32 bits
   clock: 33MHz
   capabilities: pm msi vga_controller bus_master cap_list rom
   configuration: driver=i915 latency=0
   resources: irq:91 memory:90000000-903fffff memory:80000000-8fffffff ioport:3050(size=8)


$cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 55
model name	: Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz
stepping	: 8
microcode	: 0x815
cpu MHz		: 946.268
cache size	: 1024 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms
bugs		:
bogomips	: 4326.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 55
model name	: Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz
stepping	: 8
microcode	: 0x815
cpu MHz		: 826.980
cache size	: 1024 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms
bugs		:
bogomips	: 4326.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 55
model name	: Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz
stepping	: 8
microcode	: 0x815
cpu MHz		: 501.856
cache size	: 1024 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 4
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms
bugs		:
bogomips	: 4326.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 55
model name	: Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz
stepping	: 8
microcode	: 0x815
cpu MHz		: 499.741
cache size	: 1024 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 6
initial apicid	: 6
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms
bugs		:
bogomips	: 4326.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


$sudo dmidecode -t 17
# dmidecode 2.12
# SMBIOS entry point at 0x78727000
SMBIOS 2.8 present.

Handle 0x0026, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x0025
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: Bottom-Slot 1(Left)
	Bank Locator: BANK 0
	Type: DDR3
	Type Detail: Synchronous Unbuffered (Unregistered)
	Speed: 1333 MHz
	Manufacturer: Samsung
	Serial Number: 19152225
	Asset Tag: Unknown
	Part Number: M471B5173EB0-YK0  
	Rank: Unknown
	Configured Clock Speed: 1333 MHz
	Minimum voltage:  1.350 V
	Maximum voltage:  1.500 V
	Configured voltage:  Unknown

Handle 0x0027, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x0025
	Error Information Handle: No Error
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: Unknown
	Set: None
	Locator: Bottom-Slot 2(Right)
	Bank Locator: BANK 1
	Type: DDR
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Unknown
	Part Number: Not Specified
	Rank: Unknown
	Configured Clock Speed: Unknown
	Minimum voltage:  1.350 V
	Maximum voltage:  1.350 V
	Configured voltage:  Unknown
```

Thanks in advance for any help you folks can offer.  Obviously, if there's more information that might be helpful, please let me know.

---

### Post by ian-weisser on 2015-11-28
Please describe how you can tell that a crash occurred. What changed?
Does the entire system crash? What does your systemlook like when the crash is over? Are you back at a login prompt?
Or does just one application crash?

---

### Post by SlidingHorn on 2015-11-28
> **ian-weisser said:**
> Please describe how you can tell that a crash occurred. What changed?
Does the entire system crash? What does your systemlook like when the crash is over? Are you back at a login prompt?
Or does just one application crash?

It's a complete freeze.  Keyboard & mouse responses stop, any currently playing video/audio stops, no response to pings, remote ssh attempts, etc.

Whatever is on the screen at the time stays there.  There's no "back to login" (that'd almost be preferred, lol)

---

### Post by tgalati4 on 2015-11-28
It could be a thermal shutdown.  You won't get any log messages, since the BIOS issues a halt (and catch fire) command when you trip either the CPU or GPU temperature limits.  Install *lm-sensors *and look at your temperatures just before the freeze (through ssh or an always-on-top terminal).

```
sudo apt-get install lm-sensors
sudo sensors-detect
sensors
```

---

### Post by HermanAB on 2015-11-28
Probably temperature.  Laptop designs are frequently not thermally good and don't actually perform at anything close to that which is advertised.

---

### Post by SlidingHorn on 2015-11-29
From the conky display I have running, the CPU temp has never gone beyond 58c, and everything I've read so far tells me the max would be ~100c (recommending under ~70c).  Is that really warm enough to shut it down?  I can't imagine that a (while a budget model laptop) still-on-the-market-machine wouldn't be able to handle something as basic as a bit of streaming video.

---

### Post by ian-weisser on 2015-11-29
> **SlidingHorn said:**
> It's a complete freeze.  Keyboard & mouse responses stop, any currently playing video/audio stops, no response to pings, remote ssh attempts, etc.

Whatever is on the screen at the time stays there.

Ah, then I would try the techniques at [https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash) to see if any more information can be teased out.

---

### Post by SlidingHorn on 2015-11-29
> **ian-weisser said:**
> Ah, then I would try the techniques at [https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash) to see if any more information can be teased out.

That's what I've been following, hence my mention of the logs they suggest and their lack of relevant information. :sad:

---

### Post by ian-weisser on 2015-11-29
Most developers are big fans of logging unexpected results.
No log at all is pretty bad; usually indicates a hardware fault or deep kernel issue.

Does your fan activity and case temperature near the CPU seem to match the reported 58 degrees inside?

Start finding ways to reproduce the fault reliably for testing and potentially a big report:
Does ALL intesive activity cause a freeze? Or only intensive activity from one application?
Is there a sequence of reproducible events that can reliably cause the freeze?
Is there a sequence of events booting from a LiveUSB that can reliably cause the freeze? Will the same sequence on different hardware cause the same freeze? If so, it's likely a kernel bug. If not, it's likely a hardware fault.

---

### Post by matt_symes on 2015-11-29
Hi

If it's a kernel crash, you may want to look at linux-crashdump for bug reporting.

[https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html](https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html)

You'll have to reboot to enable it.

There is talk about enabling linux-crashdump for the kernel in 16.04. 

The Ubuntu devel mailing list digest had a discussion about it on 19/11/15.

Kind regards

---

