---
title: "Site is loading very slowly"
date: 2014-07-01
forum: General Help
---

### Post by luken2 on 2014-07-01
Hi all,

I have a dedicated server installed ubuntu 14.04_LTS-server (64BITS) with xampp.
My site is loading very slowly. 

root@srv:~# netstat -anp | grep :80 | grep ESTABLISHED | wc -l
541

Check top command out put : [http://i.imgur.com/P8KEZBE.jpg](http://i.imgur.com/P8KEZBE.jpg)
It has 8gb ram.

Can you give me a solution to fix this problem. I dont have much experience with ubuntu. Please help.


```
root@srv:~# lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    1
Core(s) per socket:    8
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 77
Stepping:              8
CPU MHz:               2000.000
BogoMIPS:              4800.19
Virtualisation:        VT-x
L1d cache:             24K
L1i cache:             32K
L2 cache:              1024K
NUMA node0 CPU(s):     0-7
```

Thank you :)

---

### Post by luken2 on 2014-07-01
Anyone? Please help me

---

### Post by bob89 on 2014-07-01
Well, Ubuntu, Is good for servers, but if site is loading slow, make it unity, If that dose not work, Upgrade/alocate more RAM to your site, OR get a better iternet service provider.

---

### Post by luken2 on 2014-07-02
Anyone who can help me?

---

