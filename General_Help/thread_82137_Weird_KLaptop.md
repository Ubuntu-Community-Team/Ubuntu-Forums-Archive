---
title: "Weird KLaptop?"
date: 2005-10-25
forum: General Help
---

### Post by alvonsius on 2005-10-25
I'm currently running on Pentium M 1,6G. BAck on the days when I'm using Hoary I could get information of my processor speed when using speedstep by left clicking the KLaptop icon. So sometimes I get 700Mhz, and when in a full load I get 1,6Ghz. But now in Breezy the information is not there anymore. Is this OK? Or does my ACPI is not running the frequency scaling?

Any help??

---

### Post by daller on 2005-10-26
Open a konsole (maybe use Alt+F2 ???)

run:

cat /proc/cpuinfo

This is the output from my computer:

daniel@dallap:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor **1300MHz**
stepping        : 5
cpu MHz         : **599.642**
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2
bogomips        : 1187.20

---

### Post by alvonsius on 2005-10-26
Thanks, that's works and I know now that speedstep is running. Thanks again ...

---

