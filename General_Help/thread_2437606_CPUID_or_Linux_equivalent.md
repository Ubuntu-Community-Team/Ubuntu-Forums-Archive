---
title: "CPUID or Linux equivalent"
date: 2020-02-26
forum: General Help
---

### Post by oldbob2 on 2020-02-26
Hi folks,

apologies if this is in the wrong section, but I wasn't sure where to post it.

When I used win 7 and I wanted to overclock my PC, I used three programs to keep a check on the overclock and temps... these were OCCT, CPUZ and HWMoniter. Is there a Linux version of these, if not, what do people use when overclocking their CPU/GPU to check the clock and more importantly, the temps.

---

### Post by gsahli on 2020-02-26
This seems helpful:
[https://wiki.ubuntu.com/OverclockingCpu](https://wiki.ubuntu.com/OverclockingCpu)

---

### Post by Frogs Hair on 2020-02-26
The linked software is a start.
[https://sourceforge.net/projects/i-nex/](https://sourceforge.net/projects/i-nex/)

---

### Post by CatKiller on 2020-02-26
Conky tells me everything I want to know about how my computer's doing, at a glance. It just draws on the desktop and you can make it show whatever you want, or look however you want.

---

### Post by Yellow Pasque on 2020-02-26
If you're lucky, sensors will show you the temp without issue, and then you can monitor it with something like conky. 
```
sensors
```
Depending on what CPU you have, you may have to jump through some hoops to get the temp output, see turbo speeds, etc.

lscpu is another command to keep handy:
```
lscpu
lscpu -e
```

---

### Post by lvm on 2020-02-27
Install psensors package - it displays all the temps. CPU info including the current clock rate is available in /proc/cpuinfo.

---

### Post by oldbob2 on 2020-02-27
Thanks all, I'll give them a look in to.

---

