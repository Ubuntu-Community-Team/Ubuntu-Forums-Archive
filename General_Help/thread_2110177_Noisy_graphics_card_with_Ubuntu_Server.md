---
title: "Noisy graphics card with Ubuntu Server"
date: 2013-01-29
forum: General Help
---

### Post by Unlocker9000 on 2013-01-29
Hi.
I have a problem about a noisy fan on my AMD HD6870 graphics card in my dualboot Windows 7 and Ubuntu Server 12.04.1 pc. The fan is tempeture controlled when running Windows, but if I boot into Ubuntu server, does the fan run at full speed.
A much as I know, the fan is only tempeture controlled when the AMD drivers is loaded (the graphics card fan is also running at full speed when in BIOS and at post).
I have tried to install "fglrx", but that didn't help and it seems like the driver doesn't work with the graphics card, because when i write the command "fglrxinfo", it writes "Error: unable to open display (null)".
Thanks

---

### Post by dcstar on 2013-01-30
> **Unlocker9000 said:**
> Hi.
I have a problem about a noisy fan on my AMD HD6870 graphics card in my dualboot Windows 7 and Ubuntu Server 12.04.1 pc.

Server distros are meant for server hardware, Graphics cards are **not** server hardware and do not get supported by server software.

---

### Post by rnerwein on 2013-01-30
> **dcstar said:**
> Server distros are meant for server hardware, Graphics cards are **not** server hardware and do not get supported by server software.
hi
i really know that servers don't need a graphic card. but this post is may be a hint for the devolpers. i am running 12.04.1 (desktop) on an acer box. the funny thing is - when i boot the system up the fan sounds like a helicpoter. but when i login it's takes only a couple of second and the fan is turned down to normal (again after ! login)
cheers

---

### Post by Unlocker9000 on 2013-01-30
> **dcstar said:**
> Server distros are meant for server hardware, Graphics cards are **not** server hardware and do not get supported by server software.
I know, but it's easier to write in the terminal with a screen that without a screen.
I think I'll just gonna find an other graphics card with passive cooling and use that when running Ubuntu Server.

---

