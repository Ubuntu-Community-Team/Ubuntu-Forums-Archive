---
title: "software shutting down"
date: 2007-05-03
forum: General Help
---

### Post by Bashed on 2007-05-03
Ubuntu Feisty Fawn

All of a sudden, (even after rebooting) synaptic and add/remove are both opening, but shut down a second later. Not sure why.

The logs show this:

May  3 01:26:21 Secured dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 

May  3 01:26:21 Secured dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 

May  3 01:26:21 Secured dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name

May  3 01:26:21 Secured dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain

May  3 01:26:21 Secured dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers

---

### Post by Bashed on 2007-05-03
This is really frustrating.  First install of Ubuntu I get kernel panics. Second install I get synaptic and add/remove shutting down, even after reboot. 

I thought linux was supposed to be more stable than windows?

---

### Post by Bashed on 2007-05-03
More errors:

chad@Secured:~/Desktop/kaa-base-0.1.3$ sudo apt-get install python-dev
Segmentation fault (core dumped)
chad@Secured:~/Desktop/kaa-base-0.1.3$ sudo apt-get install python
Segmentation fault (core dumped)

---

