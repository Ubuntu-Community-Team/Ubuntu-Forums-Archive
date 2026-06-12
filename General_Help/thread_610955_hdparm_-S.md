---
title: "hdparm -S"
date: 2007-11-12
forum: General Help
---

### Post by squaregoldfish on 2007-11-12
Hi there,

I have a couple of hard disks in my machine that see long periods of inactivity, so I'd like them to sleep when they're idle.

The drives will sleep quite happily for hours at a time if I force them into standby using hdparm -y, but I can't get them to sleep after a sensible interval using hdparm -S. It works for very short values (less than a minute), but if I set the drives to sleep after something more sensible like 15 minutes, they don't power down at all.

I'm pretty sure the drives aren't being accessed because of the long sleep times I can achieve when I force them to sleep. I've also sat and watched gkrellm for the full 15 minutes (fascinating), and no activity was reported. Still no sleep though.

Has anyone else come across this, and if so have you found a solution?

Just for information, the two drives in question are Seagates: ST380020A and ST3320620A.

Thanks,
Steve.

---

