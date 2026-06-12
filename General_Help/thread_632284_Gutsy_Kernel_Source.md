---
title: "Gutsy Kernel Source?"
date: 2007-12-05
forum: General Help
---

### Post by Krusader3z on 2007-12-05
I am trying to log into my Universities wireless VPN network.

I have the vpn client installed, but when I try to run it I get this error.

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system.


At the top of the page it says:
"NOTE : Kernel Source must be installed before attempting to install the Cisco VPN client for Linux. The examples given below were from a fresh Fedora-Core-1 Linux installation. Each Linux distro will vary some."

How do i install this "kernel source" on ubuntu?

---

### Post by g2g591 on 2007-12-05
search for linux-headers in synaptic, thats the package the client is looking for, you might have to reinstall the vpn client though.

---

