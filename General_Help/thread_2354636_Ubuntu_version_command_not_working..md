---
title: "Ubuntu version command not working."
date: 2017-03-04
forum: General Help
---

### Post by Hendrik_Tans on 2017-03-04
Looking for the current version on my lap top thru the Terminal after entering:  "lsb_release -a" the screen comes back with: No arguments are permitted. How do I proceed?

---

### Post by ajgreeny on 2017-03-04
*Thread moved to **General Help**.* as a separate new thread as it had nothing to do with the large thread to which you appended it, and is more appropriate and a better fit here on its own.

I have no idea why that command is not working for you but tell us more about your version of Ubuntu, and perhaps also worth trying another of the normally available options which you can find from **man lsb_release**.
You could also try ```
sudo apt-get install --reinstall lsb-release
``` to see if that helps.

---

### Post by efflandt on 2017-03-04
I never knew the command existed. I simply:```
efflandt@msata512-1610:~$ cat /etc/lsb*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"
```But how is this for a time warp using a more universal method (the file here is SuSE-release):```
efflandt@realhost:~> ls -l /var/log/boot*
-rw-r-----    1 root     root            0 2003-05-17 18:03 /var/log/boot.log
-rw-r--r--    1 root     root        21906 2016-06-04 21:20 /var/log/boot.msg
-rw-r--r--    1 root     root        26230 2016-06-02 08:57 /var/log/boot.omsg

efflandt@realhost:~> cat /etc/*release
SuSE Linux 8.2 (i586)
VERSION = 8.2

efflandt@realhost:~> free    
             total       used       free     shared    buffers     cached
Mem:        158808     155244       3564          0      51204      12812
-/+ buffers/cache:      91228      67580
Swap:       370400        660     369740

efflandt@realhost:~> date
Sat Mar  4 16:56:12 CST 2017

efflandt@realhost:~> cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 6
model name    : Celeron (Mendocino)
stepping    : 0
cpu MHz        : 333.059
cache size    : 128 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips    : 665.19
```

---

