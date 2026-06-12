---
title: "NFS serveur 4 /etc/default/nfs-kernel-server seems to be ignore."
date: 2016-12-06
forum: General Help
---

### Post by jmjoussein on 2016-12-06
Hi,

environment : Ubuntu server 16.04 LTS serveur NFS 4

In the journalctl i have the  messages : "kernel: nfsd: too many open connections, consider increasing the number of threads"

So i have changed the option in the file /etc/default/nfs-kernel-server as following : RPCNFSDCOUNT=8 to RPCNFSDCOUNT=64

I restart the service whith systemctl restart nfs-kernel-server and i have the same log.

When i do a :

cat /proc/net/rpc/nfsd

rc 8 33197486 191137911
fh 92793 0 0 0 0
io 1111233385 2218476964
th 8 0 0.000 0.000 0.000 0.000 0.000 0.000 0.000 0.000 0.000 0.000
ra 32 0 0 0 0 0 0 0 0 0 0 0
net 224334684 10 224312219 502813
rpc 224331654 0 0 0 0
proc2 18 10 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
proc3 22 13 80496 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 10317 0 0 0
proc4 2 43007 224196064
proc4ops 71 0 0 0 12947671 6383705 172722 62147 0 0 58537422 8340744 13784 52191409 1608 50666687 3708062 0 0 8407982 0 2511 1537 198210656 0 41811 27830657 186290 371 923451 733791 14794495 13783 747576 41809 1811372 3411 3411 0 29646233 11901438 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0

and i see that th is still at 8.

Where is my mistake ?

regards,

---

### Post by jmjoussein on 2016-12-09
In fact, the solution is to reboot the server to reload the Kernel.
All the documentations says that you might reload the service nfs-kernel-server, but it doesn't work without rebooting all the server.

---

