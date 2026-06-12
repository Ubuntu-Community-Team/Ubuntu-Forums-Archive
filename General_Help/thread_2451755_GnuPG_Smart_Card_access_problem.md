---
title: "GnuPG Smart Card access problem"
date: 2020-10-10
forum: General Help
---

### Post by cyberpunk002 on 2020-10-10
Hi to everyone,

I have some troubles with accessing GnuPG smart card on Ubuntu 20.04
I got GnuPG Smart Card V3.3 and trying to setup and write on card my keys, but have some problems with accessing card.
When I run "gpg --card-edit", got message:
---
gpg: selecting card failed: No such device
gpg: OpenPGP card not available: No such device
---

GPA also can't access my card.
lsusb shows:
Bus 001 Device 002: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader

and on another laptop with windows, GPA access smart card without any problems.

anyone can help?

Thx

---

