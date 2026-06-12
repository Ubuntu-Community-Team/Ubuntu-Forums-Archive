---
title: "Memory consumption grows during execution only on Ryzen machine"
date: 2020-02-13
forum: General Help
---

### Post by jendker on 2020-02-13
I have a strange problem. I've spent the whole weekend trying to find the root cause of the unrestricted growth of memory consumption of my Python program until it turned out, that it happens only on one PC...

I run the same code on 3 machines:
- Ubuntu 18.04 PC with Intel processor (kernel 4.15.0-76-generic)
- Macbook
- Ubuntu 18.04 with AMD Ryzen CPU (kernel 5.3.0-28-generic)
and observe the linear growth of memory consumption during operation only on the last one.


I install everything in the same way on each machine: same Python version (set up with pyenv) same packages (using pip freeze) and only on Ryzen CPU based Ubuntu machine I get the growth of memory usage during operation until the process terminates or I run out of memory (please have a look on plots below).
The only thing which maybe differs Ubuntu machines apart from CPU is the kernel version, on one I am on 4.15.0-76 (where the memory consumption is stable) and on Ryzen CPU based, where I have linear growth of memory consumption I have 5.3.0-28. But I am not sure if that can be an issue...


Memory increase on Ubuntu with kernel 5.3 and Ryzen
[IMG]https://i.imgur.com/dltDH6r.png[/IMG]


Stable memory on another machine (here Mac)
[IMG]https://i.imgur.com/IGzNXJu.png[/IMG]


I will be thankful for any hints what can be the source of the problem.

EDIT: I have also tried Ubuntu 19.10 with Ryzen and I had exactly the same issue (kernel 5.3.0-29-generic).

---

### Post by EuclideanCoffee on 2020-02-13
I would try ptracing the application. I'm thinking your garbage collection isn't working on the Ryzen machine.

---

### Post by daniewicz on 2020-02-13
Can you run an older kernel on this machine: [COLOR=#000000]AMD Ryzen CPU (kernel 5.3.0-28-generic)?[/COLOR]

---

### Post by mörgæs on 2020-02-14
- or a newer, for example the daily build of 20.04?

---

### Post by mastablasta on 2020-02-14
to see what could be causing it you would need to first run the same kernel (to make sure it is not a kernel issue). if this is latest ryzen then newer kernel is a better choice.

then you need to make sure the measuring device is not reporting wrong. e.g. try to use another program to measure it.

finally i heard that ryzens are quite picky about RAM modules. some work well, while others even fail to work with them. not sure how they managed to do that as i though that these RAM chips are pretty standard. or at least they should be. so next would be to make sure RAM module is fully & officially supported by the motherboard.

---

### Post by jendker on 2020-02-14
Thank you all for the replays!

Accidentally I found this here: [https://www.reddit.com/r/Amd/comments/9mhr5q/amd_threadripper_2990wx_for_scientific_workloads/](https://www.reddit.com/r/Amd/comments/9mhr5q/amd_threadripper_2990wx_for_scientific_workloads/) which almost exactly describes my use case.
Setting `export OMP_NUM_THREADS=1` for some reason has resolved my issue, it is probably caused by PyTorch. So at the end it was not Ubuntu related...
I will try to isolate the issue and raise it at PyTorch. Thanks!

---

### Post by mörgæs on 2020-02-14
Good, if you with regards to Ubuntu consider the problem solved please mark the thread so.

---

