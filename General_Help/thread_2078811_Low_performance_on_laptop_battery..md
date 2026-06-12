---
title: "Low performance on laptop battery."
date: 2012-10-31
forum: General Help
---

### Post by skyggen on 2012-10-31
My laptop is P150x from clevo. Quad core processor and GTX560m graphics card. It runs smooth plugged but unplugged it won't even play 1080p movies. Well, everything lags. How can i fix this? Cpu governors?

---

### Post by skyggen on 2012-11-02
Anyone?

---

### Post by roudy1989 on 2012-11-02
Since I do not know any specific about NVidia's drivers (I hope you installed them), there are options to choose in AMD's control center regarding performance while A/C or unplugged. Maybe you have something similar (high performance on A/C and battery saving options while unplugged)?

Cheers!

---

### Post by skyggen on 2012-11-02
Not using Nvidia drivers. Don't know what comes default with Ubuntu 12.04 but that driver is working out much nicer than the nvidia ones. I've tried every singel nvidia driver but they make the system lag.

---

### Post by Doug S on 2012-11-03
What CPU governors is it using now, both when plugged in and when unplugged? Example, script and result:```
doug@s15:~/temp$ cat set_cpu_inquire
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
grep MHz /proc/cpuinfo
doug@s15:~/temp$ ./set_cpu_inquire
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000

```

---

