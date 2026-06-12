---
title: "Seing something in netstat I am unfamiliar with"
date: 2013-01-10
forum: General Help
---

### Post by Freshman2013 on 2013-01-10
I ran 'netstat -ap' and noticed something I am unfamiliar with: 

udp        0      0 *:mdns                  *:*         946/avahi-daemon: r 

Could someone please tell me what the 'r' after 'avahi-daemon: ' signifies?

---

### Post by dino99 on 2013-01-10
r for running

---

### Post by haqking on 2013-01-10
> **Freshman2013 said:**
> I ran 'netstat -ap' and noticed something I am unfamiliar with: 

udp        0      0 *:mdns                  *:*         946/avahi-daemon: r 

Could someone please tell me what the 'r' after 'avahi-daemon: ' signifies?

if you are asking what the service is, it is a network discovery service (zeroconf), similar to Apple's Bonojur service

---

