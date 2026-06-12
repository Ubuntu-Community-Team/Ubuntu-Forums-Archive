---
title: "Upgrading to Latest kernel"
date: 2017-03-12
forum: General Help
---

### Post by RobGoss on 2017-03-12
Hello everyone I was wondering if someone to tell me what's the best way to upgrade to the latest **kernel**, I'm currently using  **4.8.0-41-generic** and everything is running great so I guess my next question is, is it always best to use the latest Kernel with your system

I'm also running Ubuntu 16.04.2

Thanks so much

---

### Post by TheFu on 2017-03-12
When it comes to kernels, there is no "best way."  Also, running the latest isn't always smart, unless you need it.  The old "devil you know vs devil you don't know" problem.
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds) and [https://wiki.ubuntu.com/Kernel/Handbook](https://wiki.ubuntu.com/Kernel/Handbook) has more details for the lurkers. You've probably seen those already.

Folks I've seen who needed newer kernels usually had a specific issue they were experiencing and a newer kernel included the fix (or supposed fix).

I'm happily running 3.13.x on most of my systems.  If I had brand new hardware, then there might be a good reason to have a newer kernel and newer HW support.  Lacking that, I'll stay on the old standby kernels that have been proven.

---

### Post by Perfect Storm on 2017-03-12
Only if you need support for newer hardware or fixing something that doesn't work with your current kernel.
two month from now I'm going to buy Ryzen so I'll update my kernel by then.

---

### Post by Bucky Ball on 2017-03-12
> **RobGoss said:**
> ... I'm currently using  **4.8.0-41-generic** and everything is running great ...

Says it all. Any good reason to possibly break your system with a bleeding edge kernel? As mentioned, no, no reason whatsoever to be running on the latest kernel. Also mentioned, if you have very new hardware and the current kernel is having issues, then yes, that *might* be a reason to go for the latest (or a newer one). 

If you have run
```

sudo apt update
sudo apt full-upgrade
```

... then the kernel you are on is the best kernel for your install. By the looks of that kernel you are using, though, you are not using the default kernel anyway. 

You know the old saying: if it ain't broke, don't fix it, but if you do decide to go with the very latest kernel, consider it testing and don't be surprised by initial breakage or as a consequence of future upgrades. :)

PS: Have a good [read of this]("https://wiki.ubuntu.com/Kernel/MainlineBuilds#Introduction") (particularly that it is not advisable to use mainline builds on production machines) and you can find the [latest here in the 'daily' folder]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D"). Up to you. They're .deb files so it's as simple as double clicking and you're installed. I take no responsibility for any consequences. :)

---

### Post by RobGoss on 2017-03-12
Thanks for all the advice sounds good to me I'm good were I am now so maybe no reason what so ever to upgrade my kernel. I was wondering about this because I have always use the kernel that's install when I do my installations and never had any issues with any system. I guess it's a matter having the latest and greatest 

I'm old school so I'm with BuckyBall if it ain't broke don't fix it

Thanks guys for the help

---

