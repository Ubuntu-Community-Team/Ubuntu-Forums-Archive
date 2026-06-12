---
title: "Can't see all my ram"
date: 2008-05-29
forum: General Help
---

### Post by logicalfrank on 2008-05-29
Is there a maximum amount of ram Ubuntu can use? I am using 8.04 w/ the real time kernel from Ubuntu Studio for audio editing. I have six MB of ram installed. When I check my BIOS settings, it shows I have the full six installed and about five and half gigs available (my onboard video steals a half gig or so) but when I check system monitor it says I only have 2.8 gigs, which is kind of bothersome. As far as I can tell, my motherboard knows what's going on but Ubuntu needs some help. Is there something I can do to access the rest of my ram? I can get by fine on 2.8 gigs but I bought more than that.

Thanks!

---

### Post by tamoneya on 2008-05-29
are you running 64 bit or 32 bit?

---

### Post by logicalfrank on 2008-05-29
Oh sorry--32 bit. I have a 64 bit processor though so I suppose I can switch.

---

### Post by VMC on 2008-05-29
Yes the 32 bit does have a limit. I read it was somewhere around 3.2-3.3gb.
Have you tried this to see how much memory is used: 'dmesg | grep' or 'free -m'

---

### Post by tamoneya on 2008-05-29
32 bit is limited to 3.2 GB of ram unless you compile the kernel yourself.  Unless you already know how to do this I would suggest that you just switch over the the 64 bit version.  As for the 64 bit version it can theoretically support 17.2 billion GB or 16 exabytes so the thing that would be limiting you is the BIOS and your motherboard.

---

### Post by RAOF on 2008-05-29
If by "6 MB" above you mean "6 Gigabytes" of RAM, the 64bit kernel is a very good idea.  A 32bit processor can only address 4GB of RAM (2^32 ~= 4*10^9, or 4giga-thingies), although modern 32bit processors can address a bit more using what's called PAE mode.  This increases the amount of RAM addressable by the kernel (an individual application still cannot use more than 4GB) at the cost of some performance, needs to be enabled at kernel-build-time, and isn't turned on in the standard Ubuntu kernels (although the server kernel has this enabled).

Using a 64bit kernel will let you, and your applications, access all of your RAM.  And also provide a bit of a speed boost for the sorts of things Ubuntu Studio would usually be used for.

---

### Post by logicalfrank on 2008-05-29
I had *no idea* 64 vs. 32 bit architecture made a difference in how much ram you can handle. Never was an issue given that all I ever had was two gigs before. 3.3 gigs minus what my video is using would be about where I'm at now. Looks like I need to do a fresh install of the 64 bit version. Oh well--lesson learned.

And yeah, I'm not running a 486. I meant 6 GB.

---

### Post by wdaniels on 2008-05-29
> **logicalfrank said:**
> Oh sorry--32 bit. I have a 64 bit processor though so I suppose I can switch.

There is another option - the 32bit server kernel is compiled with PAE support for addressing the extra RAM, but there is a small performance hit for that and last I heard some hardware/drivers have problems with it.

In contrast, the 64bit version should yield a small performance benefit, but it does have a few issues as well (i.e. flash & java). I'd say switching to 64bit is likely the lesser of the two evils, but it is easy enough to just test the PAE kernel first to see if you have any problems before doing a reinstall.

---

### Post by Eniak on 2008-05-30
In ubuntu 32 bits desktop it sees 3gb of 4gb ram
In ubuntu 32 bits server it sees 2.9gb of 4gb
and In ubuntu 64 bits desktop it sees 2.9gb of 4gb

Anyone could point me what is going on? Since yesterday Im trying to find it out and nothing... Im running triple boot on a macbook pro (leopard, hardy and xp)

---

### Post by tamoneya on 2008-05-30
put the 64 bit liveCD in and type: ```
free -m
```in terminal and post the output here.

---

### Post by auruspex on 2008-12-24
Hello,

I figured I would bump this fairly old thread because I am experiencing the same issue on my MacBook Pro 17" with 4G of RAM installed. In both OS X and Vista Business 64, all 4G are recognized and addressed, but in Ubuntu 8.10 64 (both liveCD and full install), free -m outputs the following:

dennis@hddennis-mac:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3001       1175       1826          0         51        403
-/+ buffers/cache:        719       2282
Swap:          518          0        518

As you can see, only 3001M of RAM is getting recognized and addressed ignoring the final gig. Does anyone know what could be the potential issue here?

Thank you for your time.

---

### Post by jewblahsky on 2008-12-30
I'm having the same problem:
Ubuntu 8.10 64 bit
4 gb RAM, only 2.9 gb recognized. 
Any suggestions?

---

### Post by jewblahsky on 2009-01-06
any ideas?

---

### Post by jewblahsky on 2009-01-15
bumpity bump

---

### Post by curioshop on 2009-04-17
I am having the same problem on a lenovo x61 with ubuntu studio 8.10 amd64.  I thought maybe I really only had 3 gigs, but when I loaded slitaz linux yesterday, it reported 4.  Output of free -m is:

x@x:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2991       2972         18          0       2076         99
-/+ buffers/cache:        797       2194
Swap:            0          0          0
x@x:~$

---

### Post by curioshop on 2010-01-04
n00b mistake, i was merely wrong about the installed quantity of ram

---

### Post by underquark on 2010-01-04
I once had a 486 with 8Mb RAM and was ridiculed for spending so much on memory I would never need.  Go 64-bit.  I have XP in a Virtualbox VM, Dune2 in a box somewhere in the background and using 4789 of available 7644 Mb memory.  Java, Flash and other issues all covered in the Sticky "How-To"s.

---

