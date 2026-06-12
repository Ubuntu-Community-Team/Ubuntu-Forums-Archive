---
title: "[ubuntu] Unable to boot , urgent !"
date: 2020-11-16
forum: General Help
---

### Post by kchirowski on 2020-11-16
Hey,

I have a HP proliant server with Ubuntu on it. I recently attempted to configure a macvln interface on it by creating a script and a service to run on start .... and it did not work well. The system refused to boot. I then booted into rescue mode using a USB , mounted all partitions and removed the script and the service file i created. However, the server still refused to boot.

It directly goes to trying to boot from PXE (which i do not have) and tries that infinitly.

Using legacy boot mode, it "attempts to boot from HDD" but no further message appears and tries to go get a DHCP address. I can see the dhcp offer being sent from the DHCP server but it does not seem to be received by the faulty server. What do you recommend ?

Can it be a leftover ip route config that breaks all of this ? When going into rescue mode with the USB the network config works fine ...

Thanks.

---

