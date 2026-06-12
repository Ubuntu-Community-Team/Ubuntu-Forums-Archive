---
title: "Ubuntu 12.04 extremely slow"
date: 2013-06-17
forum: General Help
---

### Post by deathyr on 2013-06-17
Hi, i recently reinstalled ubuntu 12.04 with wubi. Before it worked perfectly, now is very very slow when moving file or installing somenthing (like after the update download). For example the browser freezes while i'm writing this message and there is only the update going on.
I think it might be related with some driver, so i would appreciate if you can say what terminal line i should type for check if this is the issue.
Version 12.04 (precise) 64 bit
Kernel Linux 3.5.0-31-generic
Memory 3,9 GiB
Intel® Core&#8482; i5 CPU 750 @ 2.67GHz × 4 
Can you tell me how to resolve this problem?

(p.s. i also tried 13.10, same problem)

---

### Post by carl4926 on 2013-06-17
Have checked what's running with 'top'

---

### Post by deathyr on 2013-06-17
I'm pretty sure it was the installation of the updates, because now that it finished everything is fine. I only closed that windows so now with top i have:
 2384 user    20   0 1239m 384m  42m S    6  9.7   4:51.13 firefox            
 1361 root      20   0  312m 105m  87m S    5  2.7   2:07.53 Xorg               
10125 user    20   0  510m  17m  11m S    2  0.5   0:00.89 gnome-terminal     
25701 user    20   0 17340 1340  956 R    0  0.0   0:00.16 top                
    1 root      20   0 24468 2332 1348 S    0  0.1   0:00.53 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.48 ksoftirqd/0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.42 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.54 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.01 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.37 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.46 ksoftirqd/1        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.02 watchdog/1         
   12 root      RT   0     0    0    0 S    0  0.0   0:00.44 migration/2        
   14 root      20   0     0    0    0 S    0  0.0   0:00.42 ksoftirqd/2        
   15 root      RT   0     0    0    0 S    0  0.0   0:00.01 watchdog/2         
   16 root      RT   0     0    0    0 S    0  0.0   0:00.37 migration/3

---

### Post by carl4926 on 2013-06-17
It seems likely
It can be a little intense, rather like the Software Centre
Which is why I use synaptic and apt-get

---

### Post by deathyr on 2013-06-17
Yes, but i have the same issue when moving file or installing any other thing, like if i can't write on the disk properly.
Is there a way to check if all my driver are optimal?

---

### Post by Impavidus on 2013-06-17
It could be that your disk is almost full. Did you make your partition large enough when reinstalling?

What do you mean exacly by "reinstalled with wine"?

---

### Post by deathyr on 2013-06-17
I had a previous installation of ubuntu 12.04 that worked really fine. Then i formatted my pc and reinstalled both windows and then ubuntu with wubi (sorry not wine, my bad) but this time is really slow.
I don't have the disk full, i made a 30 gb partition and it's just installed.
Today it also critically began to freeze when working with eclipse and a little less when watching a video.

---

### Post by carl4926 on 2013-06-17
Now I'm confused
So is this a Wubi install? Yuck!

---

### Post by deathyr on 2013-06-18
Yes, is wubi :)

---

### Post by carl4926 on 2013-06-18
If you were going to the trouble of a complete re-install, why didn't you do a proper Linux Install as well?
I can't help with Wubi, never used it

---

