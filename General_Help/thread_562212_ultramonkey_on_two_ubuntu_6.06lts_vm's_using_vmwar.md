---
title: "ultramonkey on two ubuntu 6.06lts vm's using vmware server"
date: 2007-09-28
forum: General Help
---

### Post by cslfasgard on 2007-09-28
I have followed several instruction guides to ultramonkey and no matter what I do I always get the same error.

IPVS: Error setting outbound mcast interface.
ldirectord ldirectord.cf received signal : TERM

The weird thing is I have configured the /etc/ha.d/ha.cf file for bcase, ucast, and mcast at different times troubleshooting, but the error is always mcast related regardless of how its defined.

I have two identical install ubutu vm's, both using vmware NAT for the network interface.   I have another vm hosting websites that I wish to LB. 

Has anybody successfully installed Ultramonkey 3 using HA/LB on Ubuntu and has anybody done it within VMware on Ubuntu?

I could really use some troubleshooting assistance.

Thanks in advance.

---

