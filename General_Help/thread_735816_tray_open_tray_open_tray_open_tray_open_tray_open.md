---
title: "tray open tray open tray open tray open tray open"
date: 2008-03-26
forum: General Help
---

### Post by WamBamBoozle on 2008-03-26
Hello my ubuntu brethren

My syslog, kern.log, and message files are gigabytes big and rotating them weekly doesn't stop me from running out of space on my root partition.

Why?

Because they are filled with notifications that my "tray is open". Of course, my tray is not open. How do you suppose I can get the system to stop thinking that? My dvd drives work perfectly.

Here's a sample of the logs:
```

==> /var/log/messages <==
Mar 25 22:49:58 zzz kernel: [299794.360000] end_request: I/O error, dev hda, sector 16599488
Mar 25 22:49:58 zzz kernel: [299794.364000] hdb: tray open
Mar 25 22:49:58 zzz kernel: [299794.364000] hda: tray open
Mar 25 22:49:58 zzz kernel: [299794.364000] end_request: I/O error, dev hda, sector 16599488
Mar 25 22:49:58 zzz kernel: [299794.364000] end_request: I/O error, dev hdb, sector 16010128
Mar 25 22:49:58 zzz kernel: [299794.364000] hda: tray open

==> /var/log/syslog <==
Mar 25 22:49:58 zzz kernel: [299794.360000] end_request: I/O error, dev hda, sector 16599488
Mar 25 22:49:58 zzz kernel: [299794.364000] hdb: tray open
Mar 25 22:49:58 zzz kernel: [299794.364000] hda: tray open
Mar 25 22:49:58 zzz kernel: [299794.364000] end_request: I/O error, dev hda, sector 16599488
Mar 25 22:49:58 zzz kernel: [299794.364000] end_request: I/O error, dev hdb, sector 16010128
Mar 25 22:49:58 zzz kernel: [299794.364000] hda: tray open

```

I'm running

```

root@zzz:/var/log# lsb_release -rd
Description:    Ubuntu 7.10
Release:        7.10
root@zzz:/var/log# uname -a
Linux zzz 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
root@zzz:/var/log# cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2009.382
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4021.12
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2009.382
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4018.80
clflush size    : 64

```

---

### Post by kesman on 2008-03-26
Maybe you have a setting somewhere in bios to recognize if a tray is open somewhere in the system. Try looking for it.

---

### Post by WamBamBoozle on 2008-03-29
rebooting made it go away -- you're right though -- it must have been a hardware thing

---

