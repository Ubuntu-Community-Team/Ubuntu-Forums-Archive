---
title: "Perf installation problems!"
date: 2022-08-29
forum: General Help
---

### Post by halemi on 2022-08-29
Ubuntu 22.04 (Jammy Jellyfish) 
Kernel: Linux 5.15.56
CPU: i3-8100
Motherboard: GIGABYTE H310-M

I may be dumb and there is an easy fix to this. I have problems with getting perf to work and I've done the recommendations below.

I've read that you maybe need to compile perf from linux-tools manually for this problem. But I'm not sure how to do that either 
so support for that as well would be appreciated.

[IMG]https://i.postimg.cc/bJQ1tmmV/Screenshot-from-2022-08-29-16-09-10.png[/IMG]

I am not sure what more info would be of any significance. Just ask and I'll add it.

---

### Post by halemi on 2022-09-02
Ubuntu 22.04 (Jammy Jellyfish) 
Kernel: Linux 5.15.56 (not Ubuntu standard)
CPU: i3-8100
Motherboard: GIGABYTE H310-M

I may be dumb and there is an easy fix to this. I have problems with  getting perf to work and I've done the recommendations below.

I've read that you maybe need to compile perf from linux-tools manually  for this problem. But I'm not sure how to do that either 
so support for that as well would be appreciated.

[IMG]https://i.postimg.cc/bJQ1tmmV/Screenshot-from-2022-08-29-16-09-10.png[/IMG]

I am not sure what more info would be of any significance. Just ask and I'll add it.

---

### Post by Doug S on 2022-09-02
First, you have posted this same thread 2 times now with the other one [here]("https://ubuntuforums.org/showthread.php?t=2478555&p=14110249#post14110249")
After a couple of days, you can "bump" your original post by replying to it with the text "bump", but please don't start a new thread that is the same.

Originally, it was not obvious to me that you were not using a standard Ubuntu kernel. Consider mentioning such things in your original posts. Anyway, that is the reason perf is not working for you. Ubuntu puts dependency wrapper around things like this. I know for certain that for turbostat, another linux-tools-common tool, one can simply bypass the dependency wrapper and run any other version directly from the binary location. What I NOT know is if one can do that with perf, or if perf is kernel dependant.

If it is kernel dependant, you might need to compile it yourself from the kernel source code. The code should be under the source tree at "tools/perf" and be perf.c just run "make" from there and then run it from there. I'd show an example, but it doesn't seem to compile for me on my 20.04 test server and kernel 6.0-rc3.

---

### Post by halemi on 2022-09-02
Thx for answering.

I realized that the original post were maybe posted in the wrong forum so I tried to move it but didn't manage so I re-posted it instead. 

The plan is to use perf with FlameGraph. I tried to compile perf from kernel source code but I get the same output when I try to run FlameGraph there as well.

This is what you meant, right? vvv
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[IMG]https://i.postimg.cc/7hXvxp12/Screenshot-from-2022-09-02-20-02-37.png[/IMG]
[IMG]https://i.postimg.cc/RCd2nxf3/Screenshot-from-2022-09-02-20-04-29.png[/IMG]

---

### Post by halemi on 2022-09-02
bump

---

### Post by Doug S on 2022-09-02
Instead of "perf ..." for your execution command do "./perf ..." to force the use of the one you compiled yourself instead of the Ubuntu wrapperized version.

EDIT: you could also try running the perf version for the stock Ubuntu kernel, currently 5.15.0-47. Boot to that kernel, install all the stuff needed, test it, then boot to your non-stock 5.15.56 kernel. Bypass the Ubuntu wrapper stuff and execute perf directly:

```
root@serv-jj:/home/doug# uname -a
Linux serv-jj 5.15.0-47-generic #51-Ubuntu SMP Thu Aug 11 07:51:15 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
root@serv-jj:/home/doug# /usr/lib/linux-tools-5.15.0-47/perf --version
perf version 5.15.46
```

---

### Post by dragonfly41 on 2022-09-02
When I first read this a few days ago I found some references by searching through Synaptic Package Manager - search "perf"

---

### Post by QIII on 2022-09-02
Threads merged.

Please do not create duplicate threads.  When you do, you create the situation just corrected:  more than one place where people are trying to help you creates duplication of effort and confusion, thereby watering down the community's ability to help.

---

### Post by halemi on 2022-09-03
I think this resolved it, thank you!

---

