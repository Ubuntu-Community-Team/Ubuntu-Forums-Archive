---
title: "Ubuntu randomly crashes"
date: 2008-05-29
forum: General Help
---

### Post by indy415 on 2008-05-29
Hi all i'm new to the forums so apologies in advance if I do anything wrong.

I've been using Ubuntu since Feisty Fawn and am currently on the Heron. Everything would be perfect except for one persistent error that has been here since the beginning for me. I'm running on a Rock XCTX laptop with an Nvidia go7900 graphics card(which I suspect is where the problem is ) Here's the problem:

Everything will be running just fine - sometimes for hours - then the screen flickers and everything bar the mouse, though it can only move not do anything, freezes. Sometimes, if i'm lucky, the screen will flicker again after about 10-20 seconds and Ubuntu becomes responsive again. More often than not the only thing to do is restart.

I'd really appreciate it if anybody has any ideas for me.

Thanks

---

### Post by danwood76 on 2008-05-29
When it does this does Ctrl+Alt+Backspace log you out?
This has the effect of restarting X aswell so it may stop you having to completely restart.

Which drivers are you using for the graphics card?
Is there anything in the system logs? (System -> Administration -> System Log)

---

### Post by indy415 on 2008-05-29
Hi thanks for your reply.

Unfortunately no ctrl-alt-backspace does nothing, but then it never has for some reason.

I'm currently using the nvidia restricted driver, not sure how i find out which version sorry. 

I didn't even think to check for logs (bit of a newbie). These were the last two returns to the kernel.

May 29 14:08:08 rocky kernel: [ 6750.370865] NVRM: Xid (0001:00): 7, Ch 00000000 M 00000200 D 06900000 intr 00011000
May 29 14:08:08 rocky kernel: [ 6750.387753] NVRM: Xid (0001:00): 36,  L1 -> L0

A little bit of google found this thread [http://ubuntuforums.org/showthread.php?t=24703](http://ubuntuforums.org/showthread.php?t=24703)

I'm going to try the "render accel false" option and see if that works. (though it's a shame to slow down lovely compiz).

Any other thoughts?

Cheers

---

