---
title: "ubuntu 13.10 heat issue on hp pavilion g7"
date: 2013-10-28
forum: General Help
---

### Post by hunterkasy on 2013-10-28
I have a hp pavilion g7 quad core 8 gigs of memory a 120g ssd I installed ubuntu 13.10 64 and I had the laptop shut down due to heat, when I turned it on it said that it shut down because of to high of temp.  now I have it on a laptop fan cooler and it is running between 150 -180 at idle  never had heat issues with 13.04

---

### Post by hunterkasy on 2013-10-29
still having heating issues

---

### Post by hunterkasy on 2013-10-30
anyone with some ideas that could help me out their?

---

### Post by QIII on 2013-10-30
Hello!

Can you give us some hardware specs on your graphics?

---

### Post by hunterkasy on 2013-10-30
I am giving you everything from sysinfo

> SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 13.10 (saucy) release.
	GNOME: 3.8.4 (Ubuntu 2013-09-04)
	Kernel version: 3.11.0-12-generic (#19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013)
	GCC: 4.8 (x86_64-linux-gnu)
	Xorg: 1.14.3 (15 October 2013  09:23:37AM) (15 October 2013  09:23:37AM)
	Hostname: tyler-HP-Pavilion-g7-Notebook-PC
	Uptime: 1 days 5 h 41 min

CPU INFORMATION
	AuthenticAMD, AMD A6-3420M APU with Radeon(tm) HD Graphics
	Number of CPUs: 4
	CPU clock currently at 800.000 MHz with 1024 KB cache
	Numbering: family(18) model(1) stepping(0)
	Bogomips: 2994.50
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter

MEMORY INFORMATION
	Total memory: 7459 MB
	Total swap: 222 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  ATA      
		Model:  Corsair Neutron  
	SCSI device -  scsi1
		Vendor:  hp       
		Model:  DVD A  DS8A5LH   

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
		Subsystem: Hewlett-Packard Company Device 3568
	PCI bridge(s)
		Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
		Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
		Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
		Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
		Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
		Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
		Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
		Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	ISA bridge
		Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
		Subsystem: Hewlett-Packard Company Device 3568

GRAPHIC CARD
	VGA controller
		Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] (prog-if 00 [VGA controller])
		Subsystem: Hewlett-Packard Company Device 3568

SOUND CARD
	Multimedia controller
		Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
		Subsystem: Hewlett-Packard Company Device 3568

NETWORK
	Network controller
		Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
		Subsystem: Hewlett-Packard Company Device 1629
	Ethernet controller
		Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
		Subsystem: Hewlett-Packard Company Device 3568

---

### Post by QIII on 2013-10-30
Do you use fglrx or the open source Radeon driver?

---

### Post by hunterkasy on 2013-10-30
I am using the open source Radeon driver

---

### Post by QIII on 2013-10-30
That is known to run hotter, particularly under load.

Since your APU has both the CPU cores and the GPU on the same die, increased temps from the GPU also heat up your CPU cores.

The first thing I would try is to install the fglrx (Catalyst) driver from the repo.  Take a look at the ATI driver wiki in my signature.  I typically recommend the terminal method.  If you use that, ignore my warnings about fglrx-updates and fglrx-amdcccle-updates.  I need to update the wiki.  Those work fine now.

If you don't want to try the terminal, you can install from Additional Drivers.

---

### Post by hunterkasy on 2013-10-31
i went to the additional drivers and selected the proprietary-updates and rebooted after it was done installing, so far seems to have helped the laptop the temp has dropped from 150-155 now it is running at 135-140

---

### Post by devvrathk on 2013-11-25
try installing "tlp"
try indicator-cpufreq and running your laptop at lower freq. to see if that is your problem.
also in my case, i purchased Compressed Gas Duster from amazon,
they helped me in reducing temperature by almost 10-15 C and fan noise too.

---

