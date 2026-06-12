---
title: "Random hard-locks in generic kernel"
date: 2007-10-18
forum: General Help
---

### Post by nappleapple on 2007-10-18
There was a thread talking about this or something similar in the Gutsy Development forum, which is now closed, but nothing mentioned in that thread worked.

I've been having a problem whenever I boot into the 2.6.22-14-generic kernel.  At seemingly random points, the entire system will freeze; sometimes with only mouse movement, sometimes with absolutely nothing responding.  I then have to use the Alt+SysRq commands to reboot my machine.

I've tried this with the 2.6.22 generic kernel and the 2.6.23 generic kernel with both the nvidia-glx-new package and the binary driver from NVIDIA [100.14.19].  Both setups and combinations gave me the same problem.

I have a Core2Duo processor and a GeForce 7300GS graphics card.

Everything works fine in the 386 version of the 2.6.22-14 kernel, but I would really like to utilize the other half of my processor.

---

### Post by rickggreen on 2007-10-18
> **nappleapple said:**
> There was a thread talking about this or something similar in the Gutsy Development forum, which is now closed, but nothing mentioned in that thread worked.

I've been having a problem whenever I boot into the 2.6.22-14-generic kernel.  At seemingly random points, the entire system will freeze; sometimes with only mouse movement, sometimes with absolutely nothing responding.  I then have to use the Alt+SysRq commands to reboot my machine.

I've tried this with the 2.6.22 generic kernel and the 2.6.23 generic kernel with both the nvidia-glx-new package and the binary driver from NVIDIA [100.14.19].  Both setups and combinations gave me the same problem.

I have a Core2Duo processor and a GeForce 7300GS graphics card.

Everything works fine in the 386 version of the 2.6.22-14 kernel, but I would really like to utilize the other half of my processor.


I have been crusading (forums, irc, launchpad) about this problem for over a week since I found a solution.
The problem is the multi-core cpu and the 7XXX GPUs combo. There is a regressive bug in the 100.14.19 and 100.14.11 drivers, nvidia has stated that it affects some 6XXX cards as well. The solution that nvidia says is as a work around is to use the 100.14.09 driver. 
I have found that the nvidia-glx driver (9639) will work and is in the ubuntu repros. I have been running it on my system for over a week now without any problems at all and everything works (Compiz, Google Earth, Wesnoth, Open Office, Stellarium, etc).
BTW This is not just a Ubuntu problem, I tried another distro (Mandriva 2008 Live) that defaulted to loading the 14.19 driver, the system locked within 7 mins. 
Think of a noob, wanting to switch to Linux, loading this live CD on to  pretty mainstream equipment, and it freezes up, it is a great first impression of Linux 
If we want to attract new users, the community can not just turn it's head and say, "Oh!, restricted drivers". 
We have to somehow use our leverage, to get nvidia to start working with the Linux community to  address our concerns.

---

### Post by nappleapple on 2007-10-18
> **rickggreen said:**
> I have been crusading (forums, irc, launchpad) about this problem for over a week since I found a solution.
The problem is the multi-core cpu and the 7XXX GPUs combo. There is a regressive bug in the 100.14.19 and 100.14.11 drivers, nvidia has stated that it affects some 6XXX cards as well. The solution that nvidia says is as a work around is to use the 100.14.09 driver. 
I have found that the nvidia-glx driver (9639) will work and is in the ubuntu repros. I have been running it on my system for over a week now without any problems at all and everything works (Compiz, Google Earth, Wesnoth, Open Office, Stellarium, etc).
BTW This is not just a Ubuntu problem, I tried another distro (Mandriva 2008 Live) that defaulted to loading the 14.19 driver, the system locked within 7 mins. 
Think of a noob, wanting to switch to Linux, loading this live CD on to  pretty mainstream equipment, and it freezes up, it is a great first impression of Linux 
If we want to attract new users, the community can not just turn it's head and say, "Oh!, restricted drivers". 
We have to somehow use our leverage, to get nvidia to start working with the Linux community to  address our concerns.

Installing the nvidia-glx driver in the latest Ubuntu kernel seems to work.  However, the 100.14.09 driver's kernel module doesn't like the 2.6.23 kernel and fails to compile.  Although, I think I'm set with the nvidia-glx driver.  Thanks!

---

### Post by flummoxed on 2007-10-19
I've been having the same problems since feisty... I used to just switch to the open-source nv driver, but I'll try this solution and tell you if it works or not.

I have an AMD X2 3800+ and an eVGA 7950 GT KO, by the way.

---

### Post by semateos on 2008-02-18
I am having the same problem with the newest hardy alpha release (4) using the generic-2.6.26 kernel and the nvidia-glx driver.  Can not use the nvidia-glx-new driver because my card is too old.  Anyone have any ideas?  I went through everything on the above-mentioned canonical bug-report page and it seems like all the solutions are for glx-new.  

Thanks, 
Sam

---

