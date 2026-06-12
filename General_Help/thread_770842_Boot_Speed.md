---
title: "Boot Speed"
date: 2008-04-27
forum: General Help
---

### Post by scottuss on 2008-04-27
Hi guys,

I have a very new PC, Quad core 2.4 with 2 gig memory etc and it came with Windows Vista. Vista boots to a usable desktop from cold in about 15-20 seconds. I'm very well experienced with computers (mainly Windows to be honest!) and I appreciate that Ubuntu is not Windows. However, Ubuntu takes much longer to boot and I was wondering if there is anything that I can do to  decrease this wait? I am using 64 bit Hardy 8.04

Thanks in advance!

---

### Post by ghost_ryder35 on 2008-04-27
what is "much longer"?
turn off unneeded things like
bluetooth if you dont use it
visual assistance if you dont use it
black list ipv6 if you dont need it
etc....

---

### Post by scottuss on 2008-04-27
I'm going to sound like a real moaner here! But by much longer I mean about 1 minute or so. I understand that's not much to some people, but on a machine with my spec, I feel it's too long.

Thanks for the tip by the way! I'll turn all that stuff off. :)

---

### Post by ghost_ryder35 on 2008-04-27
somethings screwy then, mine boots in about 32seconds

---

### Post by rubicon on 2008-04-27
If you want to localize the problem, you can edit GRUB menu to disable splash and allow debug messages on startup &#8212; so you could see what's happening.
Also, you can install bootchart and experiment with it.

Sorry to be so brief &#8212; I'm sleepy now and believe Google and manpages will help you much better :D

---

### Post by ghost_ryder35 on 2008-04-27
> **rubicon said:**
> If you want to localize the problem, you can edit GRUB menu to disable splash and allow debug messages on startup — so you could see what's happening.
Also, you can install bootchart and experiment with it.
 
Sorry to be so brief — I'm sleepy now and believe Google and manpages will help you much better :D
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

### Post by scottuss on 2008-04-27
> **ghost_ryder35 said:**
> [https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

Awesome! This really helped, I can see a few bits that cause problems and I've disabled them.


Cheers guys!

---

### Post by ghost_ryder35 on 2008-04-27
> **scottuss said:**
> Awesome! This really helped, I can see a few bits that cause problems and I've disabled them.
 
 
Cheers guys!
enjoy :popcorn:

---

