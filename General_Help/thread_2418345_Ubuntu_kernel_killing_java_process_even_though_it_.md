---
title: "Ubuntu kernel killing java process even though it is not out of memory"
date: 2019-05-05
forum: General Help
---

### Post by Salil_Surendran on 2019-05-05
I have an ec2 instance with 48 cores and 192 GB memory and Ubuntu 18.04. I am running a java application on it where max memory is set to be 128 GB. In between the java application gets killed by the linux kernel. I connected JVisualVM and also the GC logs is saying that the Java VM is taking just 50GB heap at max. So why is Linux killing the java application? There is nothing else running on this machine just the application. I executed dmesg and I see[166098.587603] Out of memory: Kill process 10273 (java) score 992 or sacrifice child
[166098.591428] Killed process 10273 (java) total-vm:287522172kB, anon-rss:191924060kB, file-rss:0kB, shmem-rss:0kB
[166104.034642] oom_reaper: reaped process 10273 (java), now anon-rss:0kB, file-rss:0kB, shmem-rss:0kB

---

