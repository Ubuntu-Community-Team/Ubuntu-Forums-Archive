---
title: "Apache2 only allowing localhost"
date: 2007-04-15
forum: General Help
---

### Post by Tim.R on 2007-04-15
I'm having trouble connecting to my webserver through apache2.  It can connect to itself no problem, but external connections get refused.  I tried turning off all iptables rules and setting the default to accept, and my /etc/apache2/ports.conf contains "Listen 80"

What else have I forgotten?

---

### Post by az on 2007-04-15
Does your ISP allow you to serve on port 80?

---

### Post by Tim.R on 2007-04-15
Yes, they do - I've tried from an internal network at my university (which I know for a fact should work), and from a port with my own IP from AARNET (the same ISP that ivec (ivec.org) uses) which I presume works, but don't know for certain.

---

