---
title: "what's eating my memory?"
date: 2014-02-24
forum: General Help
---

### Post by mtweldon on 2014-02-24
Still learning linux a little bit, have been out of the game for a while.. but according to System monitor I'm using 10.6GB of 16 GB and I'm only copying some files.

The most intensive thing on system monitor is chrome eating up like 500MB or so.

How can I tell what's using it all and why? When I have a fresh boot its usually around 1-2GB. doing a big rsync right now so I can't reboot.

---

### Post by tgalati4 on 2014-02-24
That's normal.  The linux kernel is designed to use up your RAM quickly, but release it just as quickly.  If you copy those files again, they will be from RAM.

Open a terminal:

```
free
```

tgalati4@Mint14-Extensa ~ $ free
             total       used       free     shared    buffers     cached
Mem:       2041968    1371892     670076          0      31792     328308
-/+ buffers/cache:    1011792    1030176
Swap:      4094972      81372    4013600

Shared memory are typically libraries that are used by multiple applications--you get greater RAM efficiency.  Store it once but use it for multiple apps.

Buffered and cached memory is freely available and will be dumped as soon as a process requires more RAM.  

So, in my example above (after 4 days of uptime), I have 1.37GB of RAM used (out of 2GB), but 670MB are shared and 1GB can be dumped when needed.  There is some swap being used but you can change the "swappiness" using a kernel parameter.


You can learn more amout linux memory managment by watching this video presentation (when available):

[https://www.socallinuxexpo.org/scale12x/presentations/whered-all-my-memory-go](https://www.socallinuxexpo.org/scale12x/presentations/whered-all-my-memory-go)

Want to drop your cache?

```
echo 1 | sudo tee /proc/sys/vm/drop_caches
```

It's your system.  Do what you want.

---

### Post by mtweldon on 2014-02-24
Ahh ok, awesome. Thanks for the information, I didn't know about that. Was just making sure everything was ok, and it looks like it is!

---

