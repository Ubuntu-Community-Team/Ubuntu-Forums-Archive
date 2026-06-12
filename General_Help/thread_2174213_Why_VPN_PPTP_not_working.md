---
title: "Why VPN PPTP not working?"
date: 2013-09-13
forum: General Help
---

### Post by emptycoder on 2013-09-13
I have a weird problem,  I have 3 PPTP VPN accounts, they connect normally with wired connection but they don't connect with Wireless connection, with message says VPN failed. Please help.

---

### Post by dcstar on 2013-09-17
> **emptycoder said:**
> I have a weird problem,  I have 3 PPTP VPN accounts, they connect normally with wired connection but they don't connect with Wireless connection, with message says VPN failed. Please help.

Make sure your Wireless ISP allows traffic on port 1723:
```
telnet whatever.the.vpn.destination 1723
```

---

