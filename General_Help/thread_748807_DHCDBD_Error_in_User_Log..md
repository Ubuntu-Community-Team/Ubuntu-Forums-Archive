---
title: "DHCDBD Error in User Log."
date: 2008-04-07
forum: General Help
---

### Post by noynac on 2008-04-07
In gutsy and now in hardy, my computer's user log repeatedly shows:

Apr  6 16:17:20 dell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu

There is a bug report on this issue that extends back to March 2007 and includes reports of this issue in Hardy:

[https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360](https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360)

Someone suggested removing DHCDBD, but this also removes network-manager and network-manager-gnome. 

Has anyone found a fix or explanation for this bug?

---

