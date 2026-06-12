---
title: "Hosting Web Server Behind Router"
date: 2008-01-02
forum: General Help
---

### Post by marshall.robert on 2008-01-02
Hi, is it possible?
ive just setup ubuntu server (compiling isp config at the mo) on an old machine and was just wondering if its possible?

---

### Post by dagnabit dang doohickey on 2008-01-02
You need to configure Port Forwarding on the router for all ports you want accessible on the WAN. Check out your router's manual and configuration panel.

---

### Post by marshall.robert on 2008-01-02
oh, right cheers

edit: instead of port forwarding, i specified the server as a dmz, a bit easier as it hosts more than one service :)

---

### Post by freymann on 2008-01-02
> **marshall.robert said:**
> 
instead of port forwarding, i specified the server as a dmz, a bit easier as it hosts more than one service :)

 I hope you have a good firewall on your machine and have it secured. DMZ means all ports are WIDE open to that box...

---

### Post by dagnabit dang doohickey on 2008-01-02
The short time spent configuring just the few (or even more than few) ports you need open is a bargain compared to the amount of time all your unnecessarily open ports will spend dangling in the DMZ.

---

