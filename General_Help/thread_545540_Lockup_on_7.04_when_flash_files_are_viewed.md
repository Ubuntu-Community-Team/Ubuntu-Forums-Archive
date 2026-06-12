---
title: "Lockup on 7.04 when flash files are viewed"
date: 2007-09-07
forum: General Help
---

### Post by calypso612 on 2007-09-07
A week or so ago my Compal HEL-80 began having issues when viewing youtube videos or listening to music on projectplaylist. While using firefox, at random moments the computer would lockup, the HD light would stay on and I wouldn't be able to run any other programs. I could still move the mouse, and sometimes type, if I opened a terminal it would but then I couldn't open another terminal and any commands run in the terminal wouldn't work. I could click the shutdown button and I would get the shutdown options however none of them worked.
Note: I am not using beryl or compiz, I have a geforce card in the laptop and it's running 7.04 Feisty Fawn with a windows XP partition. 

When I ran tail -f /var/log/messages I get this:

Sep  7 17:02:08 artimis kernel: [   39.712000] lo: Disabled Privacy Extensions
Sep  7 17:02:08 artimis kernel: [   39.712000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  7 17:02:08 artimis kernel: [   39.712000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  7 17:02:13 artimis gconfd (alyson-5541): Resolved address "xml:readwrite:/home/alyson/.gconf" to a writable configuration source at position 0
Sep  7 17:02:16 artimis dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  7 17:02:23 artimis kernel: [   54.208000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Sep  7 17:02:29 artimis dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep  7 17:02:29 artimis dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Sep  7 17:02:29 artimis dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep  7 17:02:29 artimis dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers

Any thoughts about this issue?

---

