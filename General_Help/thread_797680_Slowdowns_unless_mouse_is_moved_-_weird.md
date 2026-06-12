---
title: "Slowdowns unless mouse is moved - weird"
date: 2008-05-17
forum: General Help
---

### Post by MatthewBlack on 2008-05-17
I've got a new install of Hardy Heron on a laptop (Samsung R20). After a certain amount of time all animated graphics slow down and stutter really badly. It also happens on the default terminal application in X - the cursor will stop blinking.

However, while the mouse is being moved or the keyboard is pressed, things work fine and speed back up. So my current workaround is continuously moving the mouse around in circles. 

This has me really foxed, I've tried playing around with the xorg.conf, disabling duplicate sections, disabling the touchpad mouse in the bios, disabled compiz etc, but I can't really think what it would be :confused:. If anyone has any ideas i'd much appreciate it.

I have the propriatory ATI drivers loaded as the open source ones apparently don't work at all for my chip (too new, xpress 1250)

Thanks

Matt

---

### Post by MatthewBlack on 2008-05-17
Update - it doesn't seem to be cpu scaling - when the problem occurs, I use CPU Frequency Scaling Monitor applet to set the cpu to max and the problem is not resolved.

---

### Post by storm99999 on 2008-05-17
I had this problem for a while, and a few things helped.  One was to tell grub to boot with highres=off.  This sort of helps, but only for a few hours at best.

Another thing I tried was to try updating the kernel and compiling from source.  It requires a bit of skill, but the guide [here]("http://ubuntuforums.org/showthread.php?t=311158") which is currently updated for the version that fixed the problem for me describes a process of building the kernel that really doesn't need customization (that is as far as I know because I enjoy messing with the settings) to allay the problems.

What appears to have been the problem was that the scheduler in the kernel which tells the order of how tasks are run on the processor seems to lock up shortly after loading a graphical user interface.  Tasks begin to pile up, slowing down the system, up to the point where only moving the mouse forces all the tasks to be cleared out.

The kernel change isn't perfect, as console programs such as apt-get seem incapable of utilizing the network sometimes, dropping down to bytes a second, but it's only intermittent. 

Best of luck to fixing your problem!

---

### Post by MatthewBlack on 2008-05-17
Thanks for replying :)

I take it then that this is a kernel problem. Does it need a bug report, and if so, to whom?

---

### Post by storm99999 on 2008-05-18
I've heard that directly reporting bugs to kernel.org is a bad idea because if it isn't perfect in its reporting style, someone will get grumpy over it.  Try [https://launchpad.net/linux](https://launchpad.net/linux) , where the Ubuntu devs will look specifically at it as a problem with the (modified) Ubuntu kernel and possibly get a patch through for 2.6.24.  

It appears to have been fixed upstream in the 2.6.25.2 kernel, so even if you reported it to the kernel.org people, it won't likely get fixed in the one in Ubuntu.

---

### Post by MatthewBlack on 2008-05-18
Workaround, for anyone who comes along later with this problem:
set hpet=disable in your bootup options.

The issue has already been reported [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182063](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182063). It seems to be affecting samsung r20 laptops mostly.

As storm99999 says, it looks like its pretty much fixed in 2.6.25, so here's hoping the ubuntu people give us a patch for 2.6.24.

---

