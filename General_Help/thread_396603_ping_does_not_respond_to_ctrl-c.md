---
title: "ping does not respond to ctrl-c"
date: 2007-03-29
forum: General Help
---

### Post by ugabuga on 2007-03-29
Hi,

sometimes when I try to ping my gateway and the connection is broken, ping would start acting weirdly. It would take up to 30 sec for the first
 
**From 192.168.1.101 icmp_seq=1 Destination Host Unreachable**
 
to show up, and then the next such line could be with

 **icmp_seq=7** instead of** icmp_seq=2** 

Furthermore, in such cases if I try to terminate ping with ctrl-c it would take up to a minute until ping actually responds to the ctrl-c signal. 

This only happens when I try to ping my gateway router over a wireless (broken) connection. Also, If I try to ping a non-existent IP address, ping is working OK, meaning that icmp_seq are in order and that ping responds immediately to ctrl-c.

---

### Post by WiseElben on 2007-03-29
Try Ctrl + Z?

---

### Post by ugabuga on 2007-03-29
> Try Ctrl + Z?

No, it doesn't work. Neither does ctrl-d.

---

