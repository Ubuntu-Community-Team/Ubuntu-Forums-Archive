---
title: "Ubuntu running VERY slowly!"
date: 2007-04-23
forum: General Help
---

### Post by Pilot-Doofy on 2007-04-23
Someone told me to get a copy of my stats from the Terminal before I posted this, so I did. I think my process is governed and that's why everything is so slow at responding. Anyway...

Here are my stats:
processor : 0
vendor_id : AuthenticAMD
cpu family : 15
model : 43
model name : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping : 1
cpu MHz : 2015.162
cache size : 512 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips : 4034.42


I had the 64bit of Ubuntu installed first, but it was retardedly slow, so I thought it was the operating system because I had seen other people report the same problem with that version. But it turns out that my computer would have been fine to run the 64bit version, it's just that my processor is governed (or so I'm told).

I was wondering what you all could suggest that I do to increase performance on this thing. Because I really want to make the switch permanant from Windows to Linux, but with performance like this, I can't afford it.

---

### Post by lakersforce on 2007-04-23
Is it your entire system that is slow, or is it the graphics on your screen that is slow?

If its the graphics only it might be because your video-drivers are not installed (they are not by default if you have a ati or nvidia card).

---

### Post by Pilot-Doofy on 2007-04-23
Well, I haven't installed any graphical drivers. Do you know where I could locate some Linux drivers for my card? I looked on Nvidia's website but I couldn't find any, perhaps I wasn't looking in the right place.

I have a 6800gtx xtreme or something. It has 256mb of memory.

In addition, why does it say my Processor is "0" if it's not governed?

---

### Post by seamless on 2007-04-23
Your processor id is 0. The first core will be 0, the second will be 1. cat /proc/cpuinfo should show the first core then the second. if it's not then only one core is being used which may be your problem.

---

### Post by Dave54 on 2007-04-23
> Do you know where I could locate some Linux drivers for my card?

If you're running Feisty:
System > Administration > Restricted Drivers Manager. Check to see if a driver is recommended there. If so, it's as simple as point-and-click.

---

### Post by Pilot-Doofy on 2007-04-23
How could I make it recognize both cores?

In addition, I don't have that option when I go to System > Administration.

---

### Post by saxenaks on 2007-04-24
I am also facing similar. 7.04 is making my system too slow to use.

I noticed this error in syslog

Apr 24 12:13:53 localhost kernel: [ 5331.000000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Apr 24 12:13:53 localhost kernel: [ 5331.000000] ata1.00: cmd ca/00:08:f7:50:36/00:00:00:00:00/e0 tag 0 cdb 0x1e data 4096 out
Apr 24 12:13:53 localhost kernel: [ 5331.000000] res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr 24 12:13:53 localhost kernel: [ 5331.000000] ata1: soft resetting port
Apr 24 12:13:53 localhost kernel: [ 5331.384000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Apr 24 12:13:53 localhost kernel: [ 5331.496000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Apr 24 12:13:53 localhost kernel: [ 5331.496000] ata1.00: configured for UDMA/33
Apr 24 12:13:54 localhost kernel: [ 5331.688000] ata1.01: configured for UDMA/33
Apr 24 12:13:54 localhost kernel: [ 5331.688000] ata1: EH complete
Apr 24 12:13:54 localhost kernel: [ 5331.712000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr 24 12:13:54 localhost kernel: [ 5331.724000] sda: Write Protect is off
Apr 24 12:13:54 localhost kernel: [ 5331.724000] sda: Mode Sense: 00 3a 00 00
Apr 24 12:13:54 localhost kernel: [ 5331.744000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 24 12:13:54 localhost kernel: [ 5331.772000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr 24 12:13:54 localhost kernel: [ 5331.776000] sda: Write Protect is off
Apr 24 12:13:54 localhost kernel: [ 5331.776000] sda: Mode Sense: 00 3a 00 00
Apr 24 12:13:54 localhost kernel: [ 5331.776000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

This error is logged again and again. The system stall and then I notice this error in syslog.

---

### Post by Pilot-Doofy on 2007-04-24
this forum gets kinda slow..

---

### Post by lakersforce on 2007-04-24
Either install the "nvidia-glx" package....or, if you want the newest bleeding edge drivers for you card and an easier install,  go [here.]("http://albertomilone.com/nvidia_scripts1.html")

---

