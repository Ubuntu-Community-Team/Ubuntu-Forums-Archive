---
title: "[Solved] Dell Precision 5520 no wifi and audio - Ubuntu 16.04"
date: 2017-03-08
forum: General Help
---

### Post by joaoant on 2017-03-08
Hey guys, I have already googled a lot, tried several things but I still wasn't able to make my wifi and audio work... the wired connection works fine.
I found somewhere that installing the firmware-b43-installer package would solve it, but it didn't. 

Please, can someone help how to solve this?

After I ```
sudo lshw -C network
``` this is what I got.
```
 *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ecb00000-ecb01fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: enx9cebe84775bc
       serial: 9c:eb:e8:47:75:bc
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.08.2 duplex=full ip=202.127.29.118 link=yes multicast=yes port=MII speed=1Gbit/s
```


EDIT: Just in case someone has the same problem. It turns out that I had the .iso image of Ubuntu 16.04.1 ... for some reason even after installing it and updating everything with the third-party package I still had no wifi and audio. Then I decided to download the Ubuntu 16.04.2 iso... and it worked without any stress.

---

