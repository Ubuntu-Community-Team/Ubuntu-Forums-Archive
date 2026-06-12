---
title: "Memory Usage"
date: 2007-04-04
forum: General Help
---

### Post by gdboling on 2007-04-04
I am running Xfce 4.3 that I installed after installing ubuntu with gnome edgy eft.  I am running a Dell XPS 3.3 GHz with 1g RAM.  When I type free on the console, I get the following output.

```

            total       used       free     shared    buffers     cached
Mem:       1035344     878800     156544          0      26156     591888
-/+ buffers/cache:     260756     774588
Swap:      2409708       9936    2399772

```

When I run the system monitor it shows

255 MB used of 1011.1 MB - 25.3%
9.7 MB of 2.3 GB used swap

What concerns me the most is the difference in the used RAM.  878800 compared to 255 MB.  Which one should be more accurate?

Thanks.

---

### Post by ajmorris on 2007-04-04
> **gdboling said:**
> I am running Xfce 4.3 that I installed after installing ubuntu with gnome edgy eft.  I am running a Dell XPS 3.3 GHz with 1g RAM.  When I type free on the console, I get the following output.

```

            total       used       free     shared    buffers     cached
Mem:       1035344     878800     156544          0      26156     591888
-/+ buffers/cache:     260756     774588
Swap:      2409708       9936    2399772

```

When I run the system monitor it shows

255 MB used of 1011.1 MB - 25.3%
9.7 MB of 2.3 GB used swap

What concerns me the most is the difference in the used RAM.  878800 compared to 255 MB.  Which one should be more accurate?

Thanks.



I believe that they are both accurate:) The "used MEM" is your used virtual memory. and the "RAM" used is the amount of physical RAM in use.

---

### Post by gdboling on 2007-04-04
Thanks. I see.

---

### Post by qpieus on 2007-04-04
check out this thread:
[http://ubuntuforums.org/showthread.php?t=382874](http://ubuntuforums.org/showthread.php?t=382874)

In the first line of your output, 591888 is classified as cached. According to the thread above, this memory is really still available. That's why your system monitor output didn't count the cached mem as "used". In your second line of output, 260756 is classified as used. 260756 divided by 1024 equals 255 MB, which is what your system monitor reported as used.

That thread explains it better than I did....

---

