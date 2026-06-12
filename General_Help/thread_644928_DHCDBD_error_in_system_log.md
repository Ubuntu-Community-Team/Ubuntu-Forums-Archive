---
title: "DHCDBD error in system log"
date: 2007-12-19
forum: General Help
---

### Post by noynac on 2007-12-19
For some time, I have been getting frequent error messages in the system log as follows:

Dec 19 08:40:03 dell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

There is a lengthy bug report on this issue at:

[https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360](https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360)

One suggested solution was to remove dhcdbd. I was going to give this a try, but snynaptic also wanted to remove network-manager and network-manager-gnome. I am not on a network and do not have wireless, but I do have internet access by way of a cable modem.

Can I remove dhcdbd and the two network managers and still retain internet access?

Has anyone found a solution for this problem?

BTW, I'm now running Gutsy (Ubuntu 7.10), but I had this same problem with Feisty. My computer is a Dell 4600, and my internet access is by way of ethernet. I searched and there were some old postings on this topic but no solutions or workarounds.

Thanks for any help.

---

