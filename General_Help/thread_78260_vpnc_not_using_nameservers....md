---
title: "vpnc not using nameservers..."
date: 2005-10-18
forum: General Help
---

### Post by hajk on 2005-10-18
All seems well at first: I start vpnc with "sudo vpnc" (since vpnc-connect is missing from the vpnc package in breezy universe), supply the required information to connect to my university interactively, ending with the message that the vpn client has started in the background. 

Yet, there it stays, because it does not use the nameservers -- no nslookup possible, no pinging, no nothing. This all, despite the fact that /etc/resolv.conf lists two nameservers at the university; sudo ifconfig shows that the tun0 interface has been configured (though no traffic stats); and sudo route shows that it is the default destination.

My previous experience with vpnc was in Debian Sarge, no problem there. I wonder whether the absence of the vpnc-connect script from the breezy package breaks the package in some other way. 

Need some help here, please.

[SOLVED: see my last post this thread]

---

### Post by stefan) on 2005-10-24
I have pretty much the same problem on Breezy with the vpnc-connect script (which seems to be included now).

/stefan

---

### Post by shadow07 on 2005-10-24
I was having issues with my old distro of Breezy RC, and had issues with the Cisco VPN client.  I was told to use vpnc.  But, because it asks for the IKE group ID and password, I am unable to use it.  I then rebuilt my machine with the official release of Breezy, install the official Cisco VPN client along with gvpndialer (the GUI to the client) and all is working.

Any reason why you cannot use the official Cisco VPN client?

---

### Post by hajk on 2005-10-25
Got it solved now, problem was with the Firestarter firewall, needing some extra iptables rules, see [http://www.ces.clemson.edu/linux/nm.shtml](http://www.ces.clemson.edu/linux/nm.shtml).

---

