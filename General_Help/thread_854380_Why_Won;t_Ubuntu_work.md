---
title: "Why Won;t Ubuntu work?"
date: 2008-07-09
forum: General Help
---

### Post by IGottaWii on 2008-07-09
I installed Ubuntu via Wubi and when I booted up Ubuntu, I logged in and the resolution was sort of messed up, and I only had one dock (the one on the bottom)  no apps or anything.  I couldn't access anything.  I had to shut down my computer by holding my power button.

I installed via Wubi installer and then again with Wubi installer and the iso file.  I got the same result.  
Anything I can do to get this to run?  Thanks in advanced.

---

### Post by pytheas22 on 2008-07-09
It sounds like wubi's doing something wrong--possibly not installing everything.  You could try an installation via wubi again, but since the first two gave you the same results, I don't know if it would help.

Otherwise, the live CD would probably be a lot more reliable.  Are you able to give it a try?

---

### Post by minhmeoke on 2008-07-10
You can try adding the menu bar by right clicking on the panel, add to panel: menu bar. Then increase the screen resolution under system > preferences > screen resolution.

Also, depending on what graphics card you are using (usually Nvidia), it might be trying to use proprietary (non-Ubuntu) drivers and failing. Go to System > Hardware drivers, and try disabling or enabling it.

I would also advise you to avoid hard-reboots: do not push the power button on the computer if it freezes in Wubi, since this has a chance of causing filesystem corruption. Instead, hold the "magic" alt-sysreq combination and then press reisub to shut down the computer. [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

