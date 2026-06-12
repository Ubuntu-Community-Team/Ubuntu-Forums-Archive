---
title: "slow sleep"
date: 2007-07-05
forum: General Help
---

### Post by d1663m on 2007-07-05
I'm not sure how best to describe this and I've had a very hard time trying to find out what's causing it.

I appear to be running Ubunty Feisty. I started with the server version but added lots of the Gnome desktop packages.

```
$ uname -a
Linux swr999 2.6.20-16-server #2 SMP Thu Jun 7 20:26:23 UTC 2007 i686 GNU/Linux
```

The problem is the machine will go into som sort of partial crash mode. Instead of being fully down it's just really slow when entering any sort of wait state. Here's a prime example of the issue:

```
$ time sleep 1

real    0m15.334s
user    0m0.000s
sys     0m0.000s

```

It took over 15 real seconds to sleep for 1 second. If I run "sleep 2" the real time doubles. The system is otherwise responsive but any sleep or wait related times are multiplied. Key repeat rate slows down considerably as well (could be a factor of 15, feels about that long). Otherwise the system is still fairly responsive to anything that's already running. Simple things like "ls, cd, ps -ef" are all very quick and feel normal. Top won't start - or I'm too impatient to wait and see if it does start. 

Any idea how to capture this sort of bug? What sort of info would I need to supply if I create a bug ticket for this thing? It feels possibly kernel related, but I'd be willing to try other things like not running a GUI or reducing the number of running services to one at a time to try and eliminate other possibilites. I thought about loading the desktop kernel or building a custom one, but I thought if I could capture this bug I might help fix issues for others.

Kind regards,
Duane Meyer

---

### Post by d1663m on 2007-07-18
Wow.

Nothing?

Nobody even has one suggestion for who would be interested in such a "bug"?

---

### Post by d1663m on 2007-07-23
Seems I found something finally. It appears to mostly affect IBM Netvista variety PCs. Mines a 8305-25U.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/71023](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/71023)

The workaround is to run the kernel with the "noapic" option.

Thanks to the Ubuntu community for this support website and the bug tracking website. I was able to find a solution for my problem where I might not have otherwise.

---

