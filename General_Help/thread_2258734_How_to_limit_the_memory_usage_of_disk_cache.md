---
title: "How to limit the memory usage of disk cache?"
date: 2014-12-30
forum: General Help
---

### Post by RuralHunter on 2014-12-30
My actual problem is here: [http://ubuntuforums.org/showthread.php?t=2257348](http://ubuntuforums.org/showthread.php?t=2257348)
But no one responded. So I just want to know is there anyway to limit the memory usage of disk cache in Ubuntu? There is a vm setting in readhat but I can not find it in Ubuntu.

---

### Post by TheFu on 2014-12-30
RAM that isn't being used is wasted.  You've probably heard that.  If the RAM can be used to speed up disk performance, I'm all for it. After all, it will be dumped whenever a process needs the RAM. [https://unix.stackexchange.com/questions/90760/how-to-reduce-buffers-cache](https://unix.stackexchange.com/questions/90760/how-to-reduce-buffers-cache) explains with a quote from Redhat.

However, for systems with large amounts of RAM, being able to tune everything makes complete sense.  I would be surprised if the redhat kernel setting didn't apply to Ubuntu too - after all, a kernel is a kernel.  Did you try it?

---

### Post by RuralHunter on 2014-12-30
Yes, it didn't work:
root@server:~# echo 40 >/proc/sys/vm/pagecache
-bash: /proc/sys/vm/pagecache: No such file or directory
root@server:~# sysctl -w vm.pagecache="40"
error: "vm.pagecache" is an unknown key

---

### Post by Doug S on 2014-12-30
Are you unable to achieve your objective via increasing /proc/sys/vm/min_free_kbytes ?

---

### Post by RuralHunter on 2014-12-31
I did try vm.min_free_kbytes. The original value was 90112. I increased it to 180224 and that helped to eliminate the memory allocation error in syslog. But it didn't help with the cpu spike issue even I tried to raise it to 656636. I stopped with that value because I was afraid it might do harm to the system if I raise it too high.

---

### Post by Doug S on 2014-12-31
> **RuralHunter said:**
> I did try vm.min_free_kbytes. The original value was 90112. I increased it to 180224 and that helped to eliminate the memory allocation error in syslog. But it didn't help with the cpu spike issue even I tried to raise it to 656636. I stopped with that value because I was afraid it might do harm to the system if I raise it too high.Yes, but the thread you linked to mentions 2 gigs as the point where your troubles occur, and 10 gigs as your workaround solution. So why not try 10,000,000, or at least something more than 2 gigs? As for potential harm to your system, I don't see how. I have 16 gigs of memory total in my system and 10,000,000 works O.K. on it. Examples, after doing a bunch of memory intensive stuff:```
doug@s15:~/temp1$ [COLOR=#b22222]cat /proc/sys/vm/min_free_kbytes[/COLOR]
[COLOR=#b22222]10000000[/COLOR]
doug@s15:~/c$ [COLOR=#b22222]free -m[/COLOR]
             total       used       free     shared    buffers     cached
Mem:         15626       3312      [COLOR=#b22222]12314[/COLOR]          6         82       2903
-/+ buffers/cache:        327      15299
Swap:         8099         47       8052

doug@s15:~/temp1$ [COLOR=#b22222]cat /proc/sys/vm/min_free_kbytes[/COLOR]
[COLOR=#b22222]67584[/COLOR]    [COLOR=#b22222]<<< The default for my system[/COLOR]
doug@s15:~/c$ free -m
             total       used       free     shared    buffers     cached
Mem:         15626      12626       [COLOR=#b22222]2999[/COLOR]          6         68      12231
-/+ buffers/cache:        327      15299
Swap:         8099         73       8026
```
 Of course, for my system this is a rather extreme example at ~63% of available memory, and I did observe a performance degradation. For your system, it is only ~2.6%.

---

### Post by RuralHunter on 2014-12-31
OK. If it does no harm, I will try with 10000000. Thanks for the advice.

> **Doug S said:**
> Yes, but the thread you linked to mentions 2 gigs as the point where your troubles occur, and 10 gigs as your workaround solution. So why not try 10,000,000, or at least something more than 2 gigs? As for potential harm to your system, I don't see how. I have 16 gigs of memory total in my system and 10,000,000 works O.K. on it. Examples, after doing a bunch of memory intensive stuff:```
doug@s15:~/temp1$ [COLOR=#b22222]cat /proc/sys/vm/min_free_kbytes[/COLOR]
[COLOR=#b22222]10000000[/COLOR]
doug@s15:~/c$ [COLOR=#b22222]free -m[/COLOR]
             total       used       free     shared    buffers     cached
Mem:         15626       3312      [COLOR=#b22222]12314[/COLOR]          6         82       2903
-/+ buffers/cache:        327      15299
Swap:         8099         47       8052

doug@s15:~/temp1$ [COLOR=#b22222]cat /proc/sys/vm/min_free_kbytes[/COLOR]
[COLOR=#b22222]67584[/COLOR]    [COLOR=#b22222]<<< The default for my system[/COLOR]
doug@s15:~/c$ free -m
             total       used       free     shared    buffers     cached
Mem:         15626      12626       [COLOR=#b22222]2999[/COLOR]          6         68      12231
-/+ buffers/cache:        327      15299
Swap:         8099         73       8026
```
 Of course, for my system this is a rather extreme example at ~63% of available memory, and I did observe a performance degradation. For your system, it is only ~2.6%.

---

### Post by RuralHunter on 2015-01-04
Seems increasing vm.min_free_kbytes to 10G fixed the problem. under what condition will the reserved 10G memory be used?

---

### Post by Doug S on 2015-01-04
> **RuralHunter said:**
> Seems increasing vm.min_free_kbytes to 10G fixed the problem. under what condition will the reserved 10G memory be used?I do not know for sure, but I don't think it ever will. Think of it more as keeping enough room such that things are easier to move around and re-group and de-fragment and such. i.e. all the memory gets used, but at any given time the sum of the free chunks adds up to 10 gigs, it just would [COLOR=#b22222]not[/COLOR] be the same 10 gigs at two different times.

---

### Post by RuralHunter on 2015-01-05
> **Doug S said:**
> I do not know for sure, but I don't think it ever will. Think of it more as keeping enough room such that things are easier to move around and re-group and de-fragment and such. i.e. all the memory gets used, but at any given time the sum of the free chunks adds up to 10 gigs, it just would be the same 10 gigs at two different times.
OK. Thanks a lot!

---

