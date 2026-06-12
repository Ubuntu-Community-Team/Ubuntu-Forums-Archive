---
title: "PSensor - free memory not shown correctly?"
date: 2021-03-17
forum: General Help
---

### Post by Zlobomir on 2021-03-17
Hello,

I am running Ubuntu 20.04 with 16GB of RAM. I have lm-sensors and PSensor 1.1.5 installed. Psensor displays my free RAM as 1-2%, while both System Monitor and Task Manager show that I have 10-15% free RAM. Please see the attached screenshot of System Monitor.
Thank you in advance for your time and attention.

Best regards

---

### Post by TheFu on 2021-03-17
Use '**free -hm**'
psensor shows the "free" column for that output, so not the available, buffers, cache, or shared memory.
Most of the time, humans would think that buffers and cache should be shown as "free", since they are optional.

I've never used System Monitor and Task Manager ever.

---

### Post by Zlobomir on 2021-03-17
Thanks! Here is the output:
```

***@********:~$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           15Gi        13Gi       408Mi       209Mi       1,5Gi       1,4Gi
Swap:         8,0Gi       1,1Gi       6,9Gi
***@********:~$

```

---

### Post by TheFu on 2021-03-17
Code tags make it readable:
```
$ free -hm
     total used free shared buff/cache available
Mem: 15Gi 13Gi 408Mi 209Mi 1,5Gi 1,4Gi
Swap: 8,0Gi 1,1Gi 6,9Gi
```

What is 408Mi/15Gi?
Do all the conversions first.

---

### Post by Zlobomir on 2021-03-18
Unfortunately I am not sure. 15Gi should be the total RAM amount (1GB seems reserved for something). 408Mi appears to be the free RAM.

---

### Post by TheFu on 2021-03-18
> **Zlobomir said:**
> Unfortunately I am not sure. 15Gi should be the total RAM amount (1GB seems reserved for something). 408Mi appears to be the free RAM.

Well, 
  408Mi / 15Gi == 408Mi / 15,000 Mi (approx).  
So
  408 / 15000 = 0.0272 ... which is 2.72% free.  

The onboard GPU (commonly called the iGPU for "integrated GPU"), probably takes some RAM from the system rather than coming with dedicated RAM. That's the cheapest way to make a GPU. 1G would be within reason. It may be possible to control this iGPU RAM in the BIOS.

The "truth" here is what psensors can show.  If you want something different, you can do simple shell scripting. PSensors allows that. I've not bothered and barely concern myself over RAM use, until the system gets sluggish.  Then I close the largest RAM-using program to free 1-2GB of RAM and prevent a system crash.

---

