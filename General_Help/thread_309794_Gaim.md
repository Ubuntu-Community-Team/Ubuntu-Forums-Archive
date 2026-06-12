---
title: "Gaim"
date: 2006-11-30
forum: General Help
---

### Post by smithveg on 2006-11-30
Hi,

I have i face some problems today. After i have plug-in a pen drive and unplug. The GAIM messenger went crazy.

No matter what i do, the GAIM will automatically shutdown after i had login.
Can someone tell me, is this related to my pen drive? or any virus inside my machine. If that's a virus, how can i kill it.

I had try to uninstall the GAIM, then install again the GAIM after restart my machine. It still give me the same problems.

Someone helps me :)
smithveg

---

### Post by bapoumba on 2006-11-30
Hi,
can you start gaim from a terminal and paste the errors ?

---

### Post by pay on 2006-11-30
For about a 6 months that exact thing has happened to me and gaim 1.5. Installing gaim 2 beta5 has fixed it though.

---

### Post by smithveg on 2006-11-30
Ok, Before i upgrade into latest version. I want to trace what's actually caused this problems.

Bapoumba, can you show me the way to run GAIM in terminal. Then i show you the error. :)

Thanks.

---

### Post by PriceChild on 2006-11-30
just type ```
gaim
```into a terminal

---

### Post by smithveg on 2006-11-30
Yeah, i catch the bug, but do not know how to fix it. Do i need to upgrade into latest version now?

The bug here,
```
jimmy@jimmy-desktop:~$ gaim
Gaim has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

It is possible that this bug is already fixed in CVS.
If you can reproduce the crash, please notify the gaim
maintainers by reporting a bug at
http://gaim.sourceforge.net/bug.php

Please make sure to specify what you were doing at the time,
and post the backtrace from the core file. If you do not know
how to get the backtrace, please get instructions at
http://gaim.sourceforge.net/gdb.php. If you need further
assistance, please IM either SeanEgn or LSchiere and
they can help you.
Aborted
jimmy@jimmy-desktop:~$

```

---

### Post by raist78 on 2006-12-02
The same thing keeps happening to me.I installed the beta5 version of Gaim and after a bit of time i stay connected, it crashes saying: Segmentation fault (core dumped) ... The same thing was happening using the default Edgy version of Gaim (that's beta 3.1-1) ... i don't know what to do, except thinking on use another IM.

---

### Post by smithveg on 2006-12-02
Hi,

I do not sure how the errors come out in edgy, i'm still using dapper.
But you may try to update your gaim to version 2.0, follow the guide here, [http://repository.debuntu.org/#authentificate](http://repository.debuntu.org/#authentificate)

It helps me resolved the 'gaim shutdown automatically issues'.
Hope this helps.

smithveg

---

### Post by raist78 on 2006-12-02
I took the deb packages for gaim from debuntu, and Gaim keeps saying the error i reported on previous post... anyway, now i'm trying with the official tar.gz versione compiling it. I'll post if this procedure helps resolving the problem.

---

