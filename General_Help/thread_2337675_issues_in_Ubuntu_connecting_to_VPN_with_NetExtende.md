---
title: "issues in Ubuntu connecting to VPN with NetExtender (works in Windows)"
date: 2016-09-20
forum: General Help
---

### Post by mawxcarroll on 2016-09-20
Hi,

I have a strange issue using Sonicwall NetExtender in Ubuntu to connect to my university's VPN. First of all, when I connect through Windows I have no problems so I suspect (hope) that I can fix this on my end.

NetExtender (which uses PPP to connect to the VPN) always connects successfully. However, I cannot access anything on the remote network unless I receive certain client IP addresses:

10.10.12.26
10.10.12.30
10.10.12.33
10.10.12.34

(and possibly others - these are the only ones exposed by my testing so far)

Any other ip address that I am assigned from 10.10.12.20 and up will not work. I am completely in the dark here. If anyone has any insight into this issue I would greatly appreciate it!

Cheers,
tom

---

