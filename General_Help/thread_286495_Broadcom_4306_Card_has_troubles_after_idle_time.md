---
title: "Broadcom 4306 Card has troubles after idle time"
date: 2006-10-27
forum: General Help
---

### Post by Old Pink on 2006-10-27
Hi there

This problem basically arrives after around 30 minutes of idle internet time, and when the Internet usage is required the network manager shows the card sending, then pausing before sending again, then pausing, and continuing to send pause send pause send pause with no receiving involved. 

I'm currently using: > 02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)which I installed in Dapper, and haven't modified since the Edgy Eft change. This problem didn't occur in Dapper, only in Edgy, in all kernels, even though I didn't need to re-install in Edgy. 

I thought I'd cut the problem in the 2.6.18.1 terminal, but it looks as if it's happening the same, although less often. 

All this is solved with a reboot, and the network works fine again. It can however be very annoying to reboot at times, as I'm sure you understand.

Suggestions?

---

### Post by Old Pink on 2006-10-28
I'll try ndiswrapper.... :)

---

