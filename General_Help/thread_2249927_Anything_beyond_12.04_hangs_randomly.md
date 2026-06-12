---
title: "Anything beyond 12.04 hangs randomly"
date: 2014-10-25
forum: General Help
---

### Post by EricDP on 2014-10-25
I recently upgraded from 12.04 to 14.04. Afterwards, my system started hanging randomly, sometimes after just a couple hours of use, and the longest it went was about 32 hours. It's a full on freeze, not just X: Ctrl+Alt+Fx does nothing. SysRq+REISUB does nothing. I've tried tailing syslog and watching dmesg and there is nothing interesting logged near the hang.

I ran memtest86+ two full passes, no errors.

Assuming maybe there was a problem with the installation or upgrade process, I tried booting from a 14.04 USB (tried both 32-bit and 64-bit), and both hang after a few hours. I also tried stepping back, using a 12.10 USB that I found and it also hangs. 

Assuming it was related to newer kernel, I then tried to boot from a brand new 12.04.5 USB (using the latest 3.13.0-32-generic kernel), and the system stayed up for five full days with no problems before I had to reboot for other reasons -- so the newest 12.04 still seems good and the latest kernel seems good. But something in 12.10 and beyond is bad.

I installed a crash-dump kernel and it doesn't seem to work - still hangs and doesn't load the kernel.

Here are my devices:

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G73 [GeForce 7300 GT] (rev a1)
07:00.0 Ethernet controller: Qualcomm Atheros AR5212/AR5213 Wireless Network Adapter (rev 01)
07:01.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
ubuntu@ubuntu:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping    : 6
microcode    : 0xcb
cpu MHz        : 1596.000
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
bogomips    : 4795.30
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping    : 6
microcode    : 0xcb
cpu MHz        : 2394.000
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
bogomips    : 4795.30
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

The attached dmesg if from a 32-bit 12.04.5 boot from USB (what I'm running right now).

I've run out of ideas -- any thoughts about next steps to resolve?

---

### Post by mörgæs on 2014-10-27
There's nothing wrong with 12.04.5 but did you try a fresh install of 14.04.1 using wired internet access?

---

### Post by EricDP on 2014-10-27
I agree there is nothing wrong with 12.04.5, except that it has less life remaining and it may take some time to resolve this...

I tried booting a 14.04.1 USB, running off the USB image to ensure a clean installation. It still hangs. :(

---

### Post by mörgæs on 2014-10-28
It's not the same. The ISO running from the USB stick lacks several months' worth of updates. You have still not tried a fully updated 14.04.1.

---

### Post by EricDP on 2014-10-29
OK, I have a bare installation of 14.04.1. Now patching it...

---

### Post by EricDP on 2014-10-29
Fresh install, fully patched, system remained up for 57 minutes and is now hung. I've left it in the hung state for now in case you have any ideas for how to troubleshoot. sysreq + reisub does nothing.

---

### Post by mörgæs on 2014-10-29
Sorry, I don't have any good ideas for troubleshooting this hardware. Moving to General Help to see if you catch a better answer here.

---

### Post by EricDP on 2014-10-29
OK, thanks.

---

### Post by EricDP on 2014-10-29
Rebooted after last hang, system stayed up for 7 hours, 7 minutes. It's strange -- doesn't seem to be associated with any particular activity. It could just idle, or I could be using it. And, as noted before, with 12.04 and earlier versions of Ubuntu, it is totally solid. Typical uptime is several months, usually only rebooted with kernel patches.

---

### Post by EricDP on 2014-11-22
Bug entered:  [https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1388645](https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1388645)

---

