---
title: "dhcp option 132 on isc-dhcp-server"
date: 2019-12-14
forum: General Help
---

### Post by gekko95 on 2019-12-14
Hi folks,

Has anyone managed to set dhcp option 132 (vlan-id) with the isc-dhcp-server?

I was hoping simply adding the following to my config:

    option vlan-id "2"

would work but no luck, here is what I get back from my syslog.

Dec 14 11:46:53 XXX dhcpd[98881]: /etc/dhcp/dhcpd.conf line 7: unknown option dhcp.vlan-id

I've also tried option vlan-id code 132 = X ;  with no success.

Great forum...thanks!!

---

