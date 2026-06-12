---
title: "WINE32 in 20.04"
date: 2020-04-28
forum: General Help
---

### Post by deeteesbeard on 2020-04-28
I've just tried to install wine on 20.04LTS and fallen at the first hurdle, although that could be down to me being a relative noob.

sudo dpkg --add-architecture i386
returns
pkg-config-dpkghook: warning: Architecture q386 not defined in architecture tables, ignored

Why the "q386"?

I'm clearly missing something/s

---

### Post by wildmanne39 on 2020-04-28
Thread moved to **General Help since 20.04 is no longer in development**.

Moved to own thread from here:

[https://ubuntuforums.org/showthread.php?t=2440085](https://ubuntuforums.org/showthread.php?t=2440085)

---

### Post by deeteesbeard on 2020-04-29
Okay, thanks.

---

### Post by deeteesbeard on 2020-04-29
I've found what I was missing. It's that I wasn't paying enough attention to what I was doing.
Going though my bash history I discovered that I mistakenly initially typed "sudo dpkg --add-architecture q386"

I removed "q386" from the architecture tables with "sudo dpkg --remove-architecture q386" then carried on with the install of wine32 and wine64.

How I managed to type a q instead of an i I'm not sure, but there you go. I'm sending myself off to the corner to have a long think about what I've done.

---

