---
title: "Cisco VPN client installation error"
date: 2008-01-28
forum: General Help
---

### Post by juno_reactor on 2008-01-28
Hi there. I have the following error message when trying to install cisco vpn client : 

Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/opt/VPN 
Client/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `Client/vpnclient'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

The headers are ok the kernel is the right one and a have tried a recompilation with no result. Does anyone know mhat might be wrong??

thanx:

guitar:

---

### Post by colo on 2008-01-28
Forget the official client, get vpnc ( Package: "vpnc", Website: [http://www.unix-ag.uni-kl.de/~massar/vpnc/](http://www.unix-ag.uni-kl.de/~massar/vpnc/) ) instead. Works perfectly, without being an utter pain in the a** like the "genuine Cisco" one.

---

