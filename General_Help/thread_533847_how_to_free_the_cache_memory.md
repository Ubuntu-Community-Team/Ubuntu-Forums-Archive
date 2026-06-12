---
title: "how to free the cache memory?"
date: 2007-08-24
forum: General Help
---

### Post by adam_r on 2007-08-24
hello, after i leave my laptop on for a while (usally amule is running) when i come back i see the the memory is 13% in use and 87% cache:

```
adam@adam-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075964    2011448      64516          0      78804    1620308
-/+ buffers/cache:     312336    1763628
Swap:      1285160          0    1285160
adam@adam-laptop:~$ 
```

and i dont know why. i got 2GB memory... and this gives me **** when i try to burn anything (fails) and the overall comp seems a bit slower...

is there anyway to free or clean the cache memory?

---

### Post by aks44 on 2007-08-24
> **adam_r said:**
> this gives me **** when i try to burn anything (fails) and the overall comp seems a bit slower...

is there anyway to free or clean the cache memory?

Unlike other OSes, Linux uses your RAM the smartest way it can, ie. your applications come first, but whatever is left unused is taken by the filesystem cache, in order to speed up disk access.

Don't worry about the cache memory, whenever an application needs memory some cache is immediately freed.

Either the slowdown you are experiencing is only an erroneous impression, or it is totally unrelated to the cache memory. As for the burning problem, it *is* unrelated to cache memory.



EDIT: BTW I too have 2GB, my cache usage follows the same pattern as you, and I don't have *any* problem.

```
$ free
             total       used       free     shared    buffers     cached
Mem:       2075836    2019076      56760          0      44244    1653716
-/+ buffers/cache:     321116    1754720
Swap:      2008104          0    2008104
```


EDIT: just noticed you have CF installed. Maybe you should disable it for a while and see if you still have the same problems. Don't forget it's just a beta for now, and may contain bugs, memory leaks, ...

---

### Post by adam_r on 2007-08-24
well about the slowness you'r probebly right... because when i "compiz --replace" it pritty much fix's it. about the failed burns.. the thing is if i restart the computer (and clear the cache) the burn goes fine. and when it does fail i have no idea how to check why it failed. (i use nero & k3b)

---

### Post by rexy on 2007-08-24
```
-/+ buffers/cache:     321116    1754720
```

this is your actual memory usage, as said the cache stuff is just to speed things up, remember, unused memory is worthless memory. Try checking your memory after running for awhile before burning, however even then if your burn would fail because of memory issue's it would bomb out with an error about insufficient memory and not just silenty fail.

---

### Post by aks44 on 2007-08-24
> **adam_r said:**
> if i restart the computer (and clear the cache) the burn goes fine.

Just don't forget that when you reboot your comp, it doesn't *just* clear the cache... Believe me, the cache has nothing to do with it. The memory cache implementation is quite straightforward, no way it could have an influence on burning IMNSHO.

So your burning problem is elsewhere (even though I'm too much of a Linux newb to be able to insightfully guess what could be the cause).

---

### Post by sur on 2008-05-08
Free the cache memory by issuing this command


echo 3 > /proc/sys/vm/drop_caches


read out more here
[http://feeds.feedburner.com/~r/UbuntuUnleashed/~3/274116236/free-up-cache-memory-in-linux.html](http://feeds.feedburner.com/~r/UbuntuUnleashed/~3/274116236/free-up-cache-memory-in-linux.html)

---

