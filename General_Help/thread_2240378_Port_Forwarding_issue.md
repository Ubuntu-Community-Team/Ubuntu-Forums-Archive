---
title: "Port Forwarding issue"
date: 2014-08-19
forum: General Help
---

### Post by KishanB on 2014-08-19
Hi There,

In the last few weeks I decided to fix DNS on my network, with that I disabled DHCP on my ISP provided router and eventually successfully setup a Linux box running ISC-DHCP and BIND9, just earlier today I managed to get Squid working as a transparent proxy which is all well and good. However now I would like to forward port 3389(RDP) on my router to a PC on my internal LAN so if I type in my WAN I.P from outside my network(at work for example) I can then RDP onto my machine, this used to work but since I setup my own stuff it now does not.

As a test I setup the router to forward ports 3389 to a Linux box and ran "tcpdump -vv port 3389" on it to see if it was receiving data on that port and nothing, I've been at this for the last 4 hours and can't get anywhere.

Any help would be greatly appreciated.

Kind Regards,

Kishan

---

### Post by SeijiSensei on 2014-08-19
Is the Linux box connected directly to the Internet on one interface, or is it behind a router?

if the Linux box is the router, did you enable packet forwarding in /etc/sysctl.conf?  Remove the hash mark from net.ipv4.ip_forward=1 and reboot.

Squid doesn't need packet forwarding enabled since it just resubmits HTTP requests from the clients behind it.  Any other service which moves packets from one interface to another needs to have forwarding enabled.

---

