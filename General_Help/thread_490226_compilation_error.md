---
title: "compilation error"
date: 2007-07-02
forum: General Help
---

### Post by owl on 2007-07-02
Hello :p

I tried to compile the latest madwifi-ng drivers on my kubuntu dapper drake. I managed to apply the patch to the drivers first, but then i get some error when trying to compile:

~/lambda/madwifi-ng_0.9.3.1/madwifi-0.9.3.1$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.15-28-386/build SUBDIRS=/home/grandhibou/lambda/madwifi-ng_0.9.3.1/madwifi-0.9.3.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-386'
make[1]: *** No rule to make target `bda/madwifi-ng_0.9.3.1/madwifi-0.9.3.1'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-386'
make: *** [modules] Erreur 2

it is just told to use the "make" command, there is no need to configure, anyway i tried even but there is nothing about that. 
what about this error so?

---

