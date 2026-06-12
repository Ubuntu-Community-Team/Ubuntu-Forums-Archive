---
title: "splash screen error messages"
date: 2016-06-18
forum: General Help
---

### Post by al.adab on 2016-06-18
hello there, 

I recently re-installed Ubuntu 16.04 - and couldn't shut it down. The splash screen looked all right. I've just re-installed it twice (no dual OS, only Ubuntu) on the an Asus UX301LA (plz see further info below). After the first time, I still had the shutdown problem (splash screen still looked fine). After the second time (I've been testing it for the past half an hour) Ubuntu now shuts down no problem. On the other hand, both upon shut-down and start-up, a string of error messages appear as part of the splash screen - please see screenshot in attachment (sorry it's not very clear, had to take a picture as I couldn't figure out how to pause the splash screen). 

if useful, I'm also attaching a screenshot of my */etc/default/grub*

two questions: can these errors messages be ignored (and if not, what can I do to fix the errors)? if they can be ignored, is there anything I can do so that they don't show on the splash screen?

thank you. 


[I]$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 69
Model name:            Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Stepping:              1
CPU MHz:               800.058
CPU max MHz:           2600.0000
CPU min MHz:           800.0000
BogoMIPS:              4588.99
Virtualisation:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
NUMA node0 CPU(s):     0-3
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts[/I]

---

### Post by grahammechanical on 2016-06-18
Those are not error messages but Linux system messages. Normally we do not see them. Normally they are hidden by a splash screen. Linux loads on terminal 1 (tty1) and then loads Ubuntu on terminal 7 (tty7). Those Linux system messages are still there on tty1 but we do not see them because we see the Ubuntu desktop environment on tty7.

When we shut down Ubuntu we also switch from tty7 to tty1 again. and that is why we see those messages when we shutdown although they are Linux startup messages. Normally we do not see so many system messages. This is because the boot parameter is set to hide them. Look at this example,

> linux    /boot/vmlinuz-4.4.0-25-generic root=UUID=e32f1c10-cde2-44de-a9ab-ec108b6f2170 ro  quiet splash $vt_handoff

It is the word "quiet" that should prevent nearly all those system messages from appearing on the screen. My /etc/default/grub file has this

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Your /etc/default/grub file has this,

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= "

I have no idea if "acpi_osi= " should be there or if there should be something on the other side of the equals sign. If the system is loading and it is not taking too long, then ignore them. This is the best response that I can come up with.

Regards.

---

### Post by al.adab on 2016-06-18
thanks for the info grahammechanical

i've now noticed that they don't always appear - only after using the pc for a while (whether I re-boot or shut down). 

the "acpi_osi= " is there because that's the best answer I could find to the problem "screen brightness"/Asus keyboard: [http://ubuntuforums.org/showthread.php?t=2193133&page=3](http://ubuntuforums.org/showthread.php?t=2193133&page=3) (see post no. 23). 

is there any chance I can fine-tune the splash screen to hide those system messages? i keep coming across info about plymouth vs nvidia drivers but nothing re: intel drivers (if that have anything to do with this in the first place). 

thanks again.

---

