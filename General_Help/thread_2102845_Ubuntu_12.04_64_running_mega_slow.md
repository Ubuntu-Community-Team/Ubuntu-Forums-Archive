---
title: "Ubuntu 12.04 64 running mega slow"
date: 2013-01-08
forum: General Help
---

### Post by bobble off on 2013-01-08
HI can anybody please, please help me??

 Up in till recently I was running Ubuntu 9.10 exclusively on a old machine with a 800mhz cpu and 250mb ram and it served me very well in fact it ran much faster than my wife much newer windows laptop.

and here is my problem.. i recently started a photography business and built a new much more powerful pc:

AMD Bulldozer FX6100 cpu
8gig ram
ATI Radeon HD6670 graphics card

I did a 1st time install of the newly released Ubuntu 12.04 64bit and after the 1st boot i was greeted with error upon error then after much config editing to get the wifi working i just found it  ran much slower than my old pc so was forced to install Windows 7 for work, well windows runs like a demon super fast and my cpu load rarely goes over 10% even when editing large photos.

i deleted ubuntu and reinstalled it inside windows and now it runs with less errors and the wifi works out of the box but its still painfully slow and just hangs all the time when just web browsing never mind trying to render 1080P video files

How can i fix it i want to run ubuntu and not windows. would 32bit be more stable??

thanks in advance and for reading the whole post

---

### Post by MSPdwalt on 2013-01-08
did you run a media check? Maybe your install media was corrupt?  I've heard that can cause all sorts of fun and interesting problems.

---

### Post by bobble off on 2013-01-08
to be honest i cant remember if i checked it but the 2nd install was via wubi which i have just discovered is quite useless.

as i don't have any thing saved I've deleted and am going to try installing 12.10 if i can find a blank DVD some where and see if that's any better

---

### Post by MSPdwalt on 2013-01-08
Yeah, Wubi is Ubuntu with training wheels. Download the iso via anything but internet explorer.  I've found that IE likes to corrupt large file downloads sometimes (hence the resurgence of download managers?).  I download my .isos via torrent.  When you boot to the CD run the media check before starting install, if it passes go for it, if not, you've found problem #1.

---

### Post by MSPdwalt on 2013-01-08
Also, you want to stick with 64-bit.  32-bit can only recognize 4 gig of RAM.  Linux has had = support for 64-bit for some time now, windows in the last ~2 years has caught up now as well.  If your hardware is 64-bit capable I always recommend running 64-bit.

---

### Post by bobble off on 2013-01-08
I deleted the installation of 12.04 and tried to install a copy of 12.10 via usb following the instructions on the Ubuntu site and i now cant even install at all im getting is the purple loading screen then the screen just goes off all my fans go into overdrive and nothing. the power button wont even work and then when i reboot i get a message saying my motherboard over clock settings have been changed and failed to start.  

so is my new machine just not Ubuntu compatible?? i checked every component was except the motherboard witch for reference is a ASUS M5A 78l-mlx v2

---

### Post by bobble off on 2013-01-08
SOLVED I think lol

I decided to set my mother board to default settings which included deactivating the core unlocker and now its running. I beleve the mother board by default sees my cpu as having 4 cores instead of the 6 so will try reactivating all 6 after install and see if it slows it down again.

---

### Post by bobble off on 2013-01-08
NOT solved 

Ubuntu is seeing all 6 cores but it sees them as been only 1400mhz and not 3500mhz im going to play around with the bios/overclock setting and see if the cpu has been under clocked.

---

### Post by John.Klockenkemper on 2013-01-08
Be careful with overclocking. It is not reporting the core speed correctly and overclocking will only cause trouble. Please submit the output of this command:

cat /proc/cpuinfo

---

### Post by bobble off on 2013-01-08
this is the out put

bobble_off@bobble-off:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 1
model name	: AMD FX(tm)-6100 Six-Core Processor             
stepping	: 2
microcode	: 0x6000613
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 0
cpu cores	: 3
apicid		: 16
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips	: 6629.48
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 1
model name	: AMD FX(tm)-6100 Six-Core Processor             
stepping	: 2
microcode	: 0x6000613
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 1
cpu cores	: 3
apicid		: 17
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips	: 6629.48
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 1
model name	: AMD FX(tm)-6100 Six-Core Processor             
stepping	: 2
microcode	: 0x6000613
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 2
cpu cores	: 3
apicid		: 18
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips	: 6629.48
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 1
model name	: AMD FX(tm)-6100 Six-Core Processor             
stepping	: 2
microcode	: 0x6000613
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 3
cpu cores	: 3
apicid		: 19
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips	: 6629.48
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb

processor	: 4
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 1
model name	: AMD FX(tm)-6100 Six-Core Processor             
stepping	: 2
microcode	: 0x6000613
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 4
cpu cores	: 3
apicid		: 20
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips	: 6629.48
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb

processor	: 5
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 1
model name	: AMD FX(tm)-6100 Six-Core Processor             
stepping	: 2
microcode	: 0x6000613
cpu MHz		: 3300.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 5
cpu cores	: 3
apicid		: 21
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips	: 6629.48
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb

the only reason i mentioned overclock settings is my motherboard has a thing for under clocking my cpu every time i dont shut down properly

---

### Post by bobble off on 2013-01-08
I think i also need to and re write the wifi driver like i did with 12.04 im only geting 2mbps download when every other pc and phone in the house is geting 30mbps plus.

---

### Post by John.Klockenkemper on 2013-01-08
Please provide the output of the following commands:

lspci

lsmod

Also - Are the CPU cores underclocked by the bios?

---

### Post by bobble off on 2013-01-09
SOLVED IT 

12.10 is now installed and running fine I made some changers to the bios which included disabling "cool and quiet" this kills the cpu power to keep the fan quiet. the bios had also  under clocked by -12% power.  Just wish I could get turbo key to work in ubuntu, this is a tool provided by asus for widows that when you tap the power button it instantly overclocks the cpu to +12% without needing a reboot and turns off with a second tap.

---

### Post by vitalix on 2013-02-03
Hi. I have a similar  problem with my Ubuntu 12.04. When I installed it on my HP ProBook 4525s it worked just fine - fast and without any complains, even with Cairo-Dock panel, that could take some memory.
But after a year system stared slowing down. I always install updates and clean it up with BleachBit and Ubuntu Tweak. Sometimes I just boot in and without any program running system load is around 100%
What can take the memory?

My pc params:
AMD Athlon(tm) II P360 Dual-Core Processor 2.3 GHz
RAM 2.7

---

