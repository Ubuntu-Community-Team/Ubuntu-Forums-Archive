---
title: "Upgrade iptables for kernel 2.6.18"
date: 2006-10-16
forum: General Help
---

### Post by suba82 on 2006-10-16
hi guys I need help! I have compiled and installed kernel 2.6.18 on ubuntu. 
When I try to install new softwares with synaptic firestarter try to configure itself and I get an error. 
Iptables need to be upgraded for kernel 2.6.18

I installed iptables 1.3.6 and now I get this error 
 
Module ip_tables not found.
iptables v1.3.6: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.


can u please help me? ](*,)

---

### Post by stmiller on 2006-10-16
Looks like you didn't enable iptables in the kernel. I think you need to have the ipchains module enabled.

Try enabling these, and the other boxes listed below them.

Networking>Network Packet Filtering>Core Netfilter>Netfilter Xtable support

Networking>Network Packet Filtering>IP Netfilter>IP Tables Support

---

### Post by kitus on 2006-10-17
It works for me ....in fact, i'm using 2.18.1 kernel, great....enjoy ..Ss.:º. . Mexico. Saludos ](*,) ](*,) :mrgreen:

---

