---
title: "Image Kernel with a timing frequency of 1000Hz"
date: 2007-04-05
forum: General Help
---

### Post by c01e on 2007-04-05
Hi,

How can I get an image kernel to run at a timing frequency of 1000Hz.

Previously I've just compiled my own kernels and set in .config:
CONFIG_HZ_1000=y
CONFIG_HZ=1000

However there must be a image kernel that already does this, or a way to get a image kernel to do this.

Any thoughts?

---

### Post by cantormath on 2007-04-05
I use 
cpufreq-selector

---

### Post by c01e on 2007-04-05
mimas:~> sudo cpufreq-selector -f 1
No cpufreq support

mimas:~> sudo cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

mimas:~> lsmod | grep cpu
xt_tcpudp               4480  1 
x_tables               16132  2 xt_tcpudp,ip_tables
cpufreq_conservative     8712  0 
cpufreq_powersave       2944  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_ondemand        8876  0 

Any ideas why I'm getting "No cpufreq support", google didn't return any useful info that I could find.

---

### Post by kerry_s on 2007-04-05
sudo gedit /etc/rc.local

put-> 

exec echo 1000 > /proc/sys/dev/rtc/max-user-freq &

---

