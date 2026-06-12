---
title: "New 6.10 server - IBM 6562-92U - nothing after &quot;Starting up...&quot;"
date: 2006-12-14
forum: General Help
---

### Post by wb0gaz on 2006-12-14
A fresh install of 6.10 server boots from Grub into "Starting Up...", and then there is no further activity. If you can help me troubleshoot, please read on. Thanks!!

I'm installing 6.10 server from CDROM on a 200 MHz Pentium machine called an IBM 6562-92U ("Intellistation 300PL".) This machine is pretty old (late 90s era desktop), but I have several and have been using one of them for about 5 years as a server (using Redhat 9) with two others as hot-standby spares. I'm looking at Ubuntu 6.10 as basis for a new server load (same hardware, just new OS, and I've been standardizing on Ubuntu on several other desktop machines with excellent results.) The server has very light-duty tasks (basically Windows file sharing, ssh server, and a very few other simple tasks; it's just for personal use and isn't doing anything on the internet.)

The machine is very bare-bones; 384MB of parity RAM, a 5 GB IDE drive, an IDE CDROM, and the built-in Ethernet and video ports. It's one of several I have, and they have been very reliable as servers, so I'm pretty confident in the condition of the hardware.

When I installed 6.10 server (with nothing else on the machine, just the server itself), the installation appears to complete successfully (slowly, as it's a slow machine), without any error conditions. When I boot (into grub), I get only the "Starting up..." message, then nothing (no further disc activity, however, the disc activity LED stays lit continuously.) Only way to recover is by a power cycle.

I tried starting Ubuntu 6.10 desktop (the main installer, which runs from CDROM and lets you install), however, the video gets into an unusable state ("video mode not supported" according to my LCD panel), so I can't interact with it normally. However, it does start, and when I move the mouse (blind - remember, no display), the CDROM resumes activity, so I believe Ubuntu is running from CDROM, and this tells me there's nothing grossly wrong with the machine.

Anyway, I'm not sure how to proceed in troubleshooting, so asking for help here.

Very thanks,

Dave

---

### Post by rlozano on 2006-12-14
i suggest you try the alternate install CD instead of the live CD and use the safe mode. it may help you in your process.

---

### Post by wb0gaz on 2006-12-16
Thanks rlozano for the reply.

I tried the 6.10 alternate desktop install on your suggestion, and encountered the same problem (plus the video adapter on the motherboard is a "matrox mystique" type that's tripped up by the splash screen used during the main/live install CDROM version (same problem with a matrix G450), so I can't try that at all.)

I would guess the boot-up failure is somewhere in the grub implementation or configuration unique to ubuntu 6.10, because the kernel never starts. I was able to install fedora core 6 and puppy linux 2.12 on the same machine, each without difficulty in operation, so I am ruling out hardware problem. I need to get this system into production, so I'm going to end up with fedora core 6 rather than ubuntu 6.10 as a server; if someone reading this thread would like me to do further troubleshooting, I do have another identical machine that's on standby and I'd be glad to retry the ubuntu install and cooperate in troubleshooting in case this is a problem worth trying to solve.

Very tks,

Dave

---

### Post by rlx01 on 2006-12-16
How long did you wait?  I found that with early edge kernels I got no messages but the startup was proceeeding.  This on a normal i386 box.  After a while X started and I could login.  Now I have compiled my own kernel 2.6.19++ and I can get the messages again.

---

### Post by wb0gaz on 2006-12-17
I waited in one test about 10 minutes; it's a good point you raise (I was expecting the usual flow of kernel messages and didn't know they were supressed), however, even if there were no messages, I would be happy to hear disc activity, which was totally absent. On fedora core 6 (and puppy 2.12) kernel is up within a minute or so on the same machine (200 MHz Pentium , admittedly slow by modern standards), so I am doubtful that it's a time/speed issue.

Thanks for the posting,

Dave

---

