---
title: "New user account cannot manipulate network-manager / is a part of netdev group"
date: 2014-01-06
forum: General Help
---

### Post by ronniepinsky on 2014-01-06
I created a a new user account that cannot change network-manager settings and logon to wireless networks.  Network-manager is running but the setting "enable wireless" does not exist nor can I make any settings changes.  I have added the account to the netdev group.

This page shows it should be working:
[https://wiki.ubuntu.com/Security/Privileges#Connect_to_wireless_and_ethernet_networks](https://wiki.ubuntu.com/Security/Privileges#Connect_to_wireless_and_ethernet_networks)

Where do I go from here?

---

### Post by ronniepinsky on 2014-01-06
Sadly I had to fix this with a reboot.  I don't know where the problem came from.  I even tried restarting network-manager and deleting it's state file.  I also tried unlocking the interface with rfkill. The configuration file did not look unusual.

---

