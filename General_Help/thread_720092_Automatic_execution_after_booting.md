---
title: "Automatic execution after booting"
date: 2008-03-09
forum: General Help
---

### Post by jsatubnutufroums on 2008-03-09
Hi, experts:
I write a program and want this program to be executed when PC boots or networking restarts. I would like to execute this program after DHCP client is already allocated a IP address. What should I do? Thank you.

---

### Post by dcstar on 2008-03-10
> **jsatubnutufroums said:**
> Hi, experts:
I write a program and want this program to be executed when PC boots or networking restarts. I would like to execute this program after DHCP client is already allocated a IP address. What should I do? Thank you.

/etc/rc.local

---

### Post by jsatubnutufroums on 2008-03-10
> **dcstar said:**
> /etc/rc.local
I find this information "/etc/rc.local is almost the last script called at boot up". Thank you.
When users execute '/etc/init.d/networking restart', I also want to restart my local daemon. What should I do?

---

