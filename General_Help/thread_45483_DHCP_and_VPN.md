---
title: "DHCP and VPN"
date: 2005-06-30
forum: General Help
---

### Post by RossC0 on 2005-06-30
I've connected to my works VPN - but my resolv.conf keeps getting re-written  even though I've changed its mode to 444.

I only work at home every so often - but its a pain as it happens throughout the day and causes problems with email and gaim!

Any ideas how best to stop this / or how to setup my VPN so that it doesnt happen ?

---

### Post by intangible on 2005-06-30
A temp fix would be to just stop dhclient (sudo killall dhclient3).  I hope someone gives you a more perm. solution.

I'll be watching this thread because this will be useful to me also.

---

### Post by RossC0 on 2005-07-15
I've installed pptpClient - which makes connecting to the VPN a breeze!

But still no decent solution on the resolv.conf being overwritten apart from editing the code that rewrites it and stopping the function - but when I forget and reboot I get no DHCP !!

---

