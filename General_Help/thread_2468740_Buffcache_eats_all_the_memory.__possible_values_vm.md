---
title: "Buff/cache eats all the memory.  possible values vm.vfs_cache_pressure"
date: 2021-11-09
forum: General Help
---

### Post by glorsh66 on 2021-11-09
Buff/cache eats all the memory which leads to use of the swap.  what are the possible values of vm.vfs_cache_pressure and vm.swappiness?




I have some proprietary software installed on my server which includes a lot of databases - postgress, tarantool, Memcached, and several proprietary high load applications. 
The system is **ubuntu 16.04 4.15.0.76-generic**


Also on the same machine, I have a virtual machine installed (quemu/kvm) that has all the same software but a different version (it is the reason why it is installed on a virtual machine). guest system **ubuntu 18.04 5.4.0-84-generic**




The main thing about this software is that I have a very limited amount of available options, and most importantly it has quite strict **timeout** values, which I cannot increase. (less than half a second). 


So the problem is that after some time, all the free memory goes to buff/cache, and after this, the system starts to use swap.




I tried to set **vm.swappiness = 3** from default **60**, it helped somehow, but the system doesn't work really stable, so it is more like I prolonged its agony) 
Using swap leads to increased timeouts, which in turn leads to not working application.
For some reason, the system prefers to start using swap, than flushing cache/buff.




After some more reading, I found that I can manually clean the buff cache.
So I tried using **/bin/sync && /bin/echo 3 > proc/sys/vm/drop_caches**
I made it in a crontab job which runs every two hours for the host system and every six hours for the guest system. 
I have tried this for a week the system seems to work stable, I haven't found any corrupted files yet.
I tried to use it on the host and the guest machines.


Is it safe to use **/bin/sync && /bin/echo 3 > proc/sys/vm/drop_caches**?
So sources say that it may lead to data loss (mostly because there is some time between **sync && echo 3 >  proc/sys/vm/drop_caches**).






How **vm.swappiness and vm.vfs_cache_pressure** are related?
How does **vm.swappiness** work in the same way for these versions:
```

Ubuntu 16.04 4.15.0.76-generic 
Ubuntu 18.04 5.4.0-84-generic

```


If it set **vm.swappiness = 0** does it mean that the system will never use swap at all, and terminate all the processes if memory is not enough?
I have read somewhere that Linux kernel developers changed the behavior of **vm.swappiness = 0** starting from some kernel version, so if set to zero 0, it just kill the process.


What are the possible values for **vm.vfs_cache_pressure**
Some sources say that it is from **0 to 200.**
Different sources say that it determines the number of memory pages that can be allocated for buff/cache.
What is the real meaning of vm.vfs_cache_pressure?
What are the possible values that I can set for vm.vfs_cache_pressure?
Will setting *vm.vfs_cache_pressure = 200* help remedy my problem? 
is there a way to completely prohibit using buff/cache if it leads to using swap?


What other options can I try?
How can I see what files, what objects are cached? 


Are there any other options except for *vm.vfs_cache_pressure* and *vm.swappiness *that can change usage, the priority of buff/cache? 


The idea is to **not use swap** if there is some memory available (not free) and prioritize flushing cache/buff and only if this is not possible and only then to use swap (to prevent terminating process) and of course don't terminate processes if there is available swap.

---

### Post by ActionParsnip on 2021-11-09
The VM Swappiness will help a lot but keeping things in RAM is good because it is significantly faster than your permanent storage. The kernel knows what it's doing. Let it do its job

---

### Post by Impavidus on 2021-11-09
The buffers/cache is mostly for reading (I think). Files written to disk get flushed quite soon, but files (both reading and writing) can be kept in memory a long time for faster access if you want to read them again. The downside is that memory used by applications may be send to swap instead, which is not so nice if you need that memory again before you need the file again. Linux does a decent job of guessing this correctly, but sometimes it fails.

The main use of swap these days is to give the user a warning by slowing down that he's running out of memory, so that the user can quickly close some applications before things start to crash. On a server, that doesn't apply. You could consider running your server without any swap. Then it won't be used.

Have you subscribed to the extended security maintenance for your 16.04 system? Because otherwise 16.04 is no longer spported. Your kernel versions appear a bit old. I'd expect 4.15.0-162 and 5.4.0-90.

---

### Post by glorsh66 on 2021-11-10
Thanks! No, the problem that the server is running in a disconnected environment so it hasn't access to the internet.
So I had to use apt-mirror to update my systems.

But what values can **vm.vfs_cache_pressure**&#8203; take?

---

