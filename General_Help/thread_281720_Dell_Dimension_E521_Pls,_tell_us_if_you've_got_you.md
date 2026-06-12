---
title: "Dell Dimension E521: Pls, tell us if you've got yours working"
date: 2006-10-21
forum: General Help
---

### Post by NRios on 2006-10-21
I've found several people in this forum having the same problem with a Dell Dimension E521 (Athlon 64 X2, nVidia nForce chipset) -- the mouse pointer freezes in Dapper and Edgy.

If you have this model of computer and have not found this problem, please, let us know.

Thanks!

.Nacho.

---

### Post by NRios on 2006-10-23
The mouse pointer freezes in Dapper and Edgy with i386 or AMD-optimized kernel, SMP or not. Debian Etch does not work either.

---

### Post by pregoeater on 2006-11-02
did you get the monitor with the system if so use the usb hub on it and no more mouse freezes thats what i did....or use a usb hub.

---

### Post by madhadron on 2006-11-28
I just got my E521 working, and let it run (while doing my normal work on it) for a day or so just to make sure everything was stable.  I just posted a Howto in the howto forum (but it hasn't shown up yet).

---

### Post by toto22 on 2006-12-16
USB didn't run at the beginning with keyboard and mouse. Since I use the kernel arguments usb-handoff and i8042.nomux that part is fine. 
I couldn't make the dual core run though, despite I believe to use the right kernel:

```
uname -a
Linux Linux 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
```
 
```
more /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2000.000
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3d
now pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 4014.54

```

I bougth the system with an ATI 1300pro and couldn't enable 3d acceleration, but that part doesn't bother me. 

Strangely the system also hangs frequently on shut-down.

---

### Post by montalbano on 2006-12-22
hi folks,

tried the workaround with an additional pci-usb - card and having put off the usb-controller in bios. actually, it works fine IN ubuntu....

BUT: the problem is in GRUB. of course, the pci-card isn't ready at the time GRUB starts, so there is no choice to make because the keyboard doesn't work at that time!!

Any ideas about this problem?

thanx and greez from cold switzerland

---

### Post by szf on 2006-12-22
Read more about problems with this Dell series at this [forum]("http://forums.us.dell.com/supportforums/board/message?board.id=sw_other&message.id=54328&view=by_date_ascending&page=1").

---

### Post by toto22 on 2006-12-30
I plugged my keyboard directly then it works in grub. 
To make if work in Ubuntu I used the Kernel Arguments: 
usb-handoff i8042.nomux

Works for me fine. I use the std. Dell Keyboard and a Logitech Optical USB mouse

---

### Post by magicfab on 2007-01-24
This is a known issue fixed by updating to the latest BIOS from Dell. See:
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries)

---

