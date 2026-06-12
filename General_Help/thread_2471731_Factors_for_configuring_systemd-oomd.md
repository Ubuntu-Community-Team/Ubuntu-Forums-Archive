---
title: "Factors for configuring systemd-oomd?"
date: 2022-02-07
forum: General Help
---

### Post by bcschmerker on 2022-02-07
**I've at least one, possibly three AMD64 systems candidate for 22.04-LTS, and systemd-oomd is a definite new-to-me.**  The currently-down Hot Rod gPC is due for an upgrade planar, probably a GIGABYTE® GA-MA785GM-US2H or GA-MA785GM-UD2H (as both are compatible with my existing signal cabling and disquette/HDD/ODD installation and can take 4 UDIMMs of different-speeds memory, 2 GiB per module).  The ASUS® CM1630's days on Windows are numbered, as it doesn't qualify for Win 11; I cannot rule out an upgrade planar in the form of an M4A78LT-M or M5A78LT-M/USB3 (the complete version with planar EIA 571 and IEEE 1284 ports off the Super-I/O).  What exactly *is* memory pressure?  swap pressure?  I'm unable to find a programmer's guide to oomd, therefore at a loss to determine acceptable memory and swap pressures for configuration.

---

### Post by KBar on 2022-02-07
Recently, I read about swapping and memory management in general. Perhaps there are answers to your questions in one of these[SUP][[1]("http://git.cmpxchg.org/cgit.cgi/linux-psi.git/commit/?id=eb414681d5a07d28d2ff90dc05f69ec6b232ebd2")][/SUP] sources[SUP][[2]("https://lwn.net/Articles/759781/")][/SUP]?
[HR][/HR]
[LIST=1]
[*]Patch that enabled PSI: [http://git.cmpxchg.org/cgit.cgi/linux-psi.git/commit/?id=eb414681d5a07d28d2ff90dc05f69ec6b232ebd2](http://git.cmpxchg.org/cgit.cgi/linux-psi.git/commit/?id=eb414681d5a07d28d2ff90dc05f69ec6b232ebd2) 
[*]LWN.net article about PSI: [https://lwn.net/Articles/759781/](https://lwn.net/Articles/759781/) 
[/LIST]

---

