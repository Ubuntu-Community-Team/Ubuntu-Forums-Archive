---
title: "Drag file freezes Hardy Nautilus"
date: 2008-04-27
forum: General Help
---

### Post by BrownieBoy on 2008-04-27
Whenever I try to drag a file from Nautilus, my desktop crawls to an almost halt.  You can see the cursor moving in slow motion, but neither Ctrl-Alt-Backspace or Ctrl-Alt-Del will break out of it.  Sometimes the desktop (not the machine) will spontaneously restart itself.  Sometimes I have to hit the power switch.

It only happens when Desktop Effects is enabled (any level).  No probs at all when it's disabled.

I'm running the Nvidia Restricted Driver from out of the repository on a GeForce 8800 GTS card.  It's a completely clean Hardy install.

---

### Post by kawaji on 2008-04-28
Hi,


Which ubuntu your compiz is running on ? 

Another user have been posted almost the same problem in japanese ubuntu forum.
He checked errors by dmesg, and found an error.
> [ 7345.598551] compiz.real[15026]: segfault at 80 rip 40fee0 rsp 7fffb9632480 error 4

He is using ubuntu 8.04 amd64, AthlonX2 BE2400, memory 4Gb, ECS GeForce6100PM-M2, GeForce8600GT.

I have installed ubuntu 8.04 i386 , athlon64, ati redeon x1600XT, and got no such problem.

---

### Post by BrownieBoy on 2008-04-28
Thanks for your reply, Kawaji.

The problem has stopped now, but I'm not sure what I changed to cause that.  I installed one of the simple settings manager for Compiz Fusion and set it to "Hollywod ain't got nothing..." setting - yes, it really is called that - and the problem stopped.

Odd that actially maxing out my Compiz effects should cure the problem, isn't it?

I'm using Ubuntu 8.04 generic, dual-core AMD Opteron, 2 gig of RAM and GeForce 8800 GTS video card.

---

### Post by BrownieBoy on 2008-04-30
I spoke too soon.  The problem has returned.

Copying from or to USB devices seems more prone to triggering it, but I've seen it using purely internal drives too.  I'll check dmesg the next time I'm on Hardy.  I'm back on Gutsy now, out of frustration.

---

### Post by BrownieBoy on 2008-04-30
I checked dmesg and there's no segfault errors in there.  There's nothing else that says "Compiz" either.

---

### Post by kawaji on 2008-05-01
Is this your post?
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/224360]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/224360")

> 1) Enable compiz. Exact settings seem to be irrelevant. I disabled them all and the problem was still evident.
2) Open a nautilus window containing some icons.
3) Enable list mode.
4) Ensure there are enough columns of information such that horizontal scrolling of the window would be require to see them all.
5) Begin to drag an icon.
6) The desktop will *almost* freeze. Some small and intermittent mouse movement may occur. However, the only way to rectify the situation is via a force kill of X (e.g., alt - sys req - k).

Repeating the above steps except with step 4 having no horizontal scrolling will not entice the problem.

---

### Post by BrownieBoy on 2008-05-01
> **kawaji said:**
> Is this your post?
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/224360]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/224360")

@Kawaji,

No, it's not.  That's definitely the same bug though.  I always use List Mode, and he's right: it doesn't happen under Icon Mode.  I've posted a confirmation follow-up on his report.

Many thanks for spotting this.

---

### Post by kawaji on 2008-05-01
I also read coz's post in CF forum.

hmm...

Everybody having the same problem seems to be using the same version of nvidia driver.

---

### Post by BrownieBoy on 2008-05-01
> **kawaji said:**
> I also read coz's post in CF forum.

hmm...

Everybody having the same problem seems to be using the same version of nvidia driver.

Indeed.  But that happens to be the version of the driver that's in the Hardy repositories at present.  It appears to be the same one that's available on the Nvidia site too.

I've directed Coz to the bug report that you found.

---

### Post by BrownieBoy on 2008-05-06
Problems now gone for me.  Got some updates from the repositories this morning, so I'm guessing that fixed it.

---

### Post by webaake on 2008-05-10
Seems I have the almost the same problem when trying to copy files from a nfs volume when in list mode, to a local HD. When in icon mode it's OK.

---

