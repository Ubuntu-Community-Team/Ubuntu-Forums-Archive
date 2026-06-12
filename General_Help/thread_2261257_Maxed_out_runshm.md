---
title: "Maxed out /run/shm"
date: 2015-01-17
forum: General Help
---

### Post by prenger745 on 2015-01-17
Hello Everyone,

I am working on installing some camera monitoring software (Zoneminder).  It is installed on Ubuntu 14.04 and is working great with 3 cameras.  When I add a fourth it stops getting streams from some of the cameras.  I have tracked this down to a maxed out /run/shm.

df-h produces the following (this is with 3 cameras running):


Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       228G  1.9G  214G   1% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            986M  4.0K  986M   1% /dev
tmpfs           200M  576K  199M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            997M  816M  181M  82% /run/shm
none            100M     0  100M   0% /run/user

Notice /run/shm is at 82%.  If I add a fourth camera /run/shm goes all the way to 997M and the feeds start crashing out.  I guess simply put, is there anyway to make the size of the /run/shm greater than 997M?

Thanks,
Dan

---

### Post by efflandt on 2015-01-18
/run/shm is shared memory in RAM, so it sounds like you need more RAM (or swap).  Although, using virtual memory (swap) could result in things slowing down.

With 8 GB RAM mine shows 3.9 GB available for /run/shm and /dev (I do not have any swap):```
efflandt@XPS-8100-1404:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4       414G  181G  212G  47% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           792M  1.4M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  668K  3.9G   1% /run/shm
none            100M   60K  100M   1% /run/user
```

---

### Post by ibjsb4 on 2015-01-18
Yes, default is half of the physical ram.  So this tells us that you have 2G of ram.  And looking through the Zoneminder docs, I find:
> You may get a system that works with one or two cameras going on an old P200 but you will be able to support more cameras, at a higher frame rate, with faster machines with more RAM. More guidance is available on the web forums.
and
> Although the camera will can capture high res, you don't have enough RAM currently to do so. Especially if you have the early 256MB model. So just stick to 640x480.  You should be able to get around 20fps, but if you do anything involving the CPU you will get underruns.

---

