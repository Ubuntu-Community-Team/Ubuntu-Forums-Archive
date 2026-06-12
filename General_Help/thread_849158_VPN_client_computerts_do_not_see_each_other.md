---
title: "VPN client computerts do not see each other"
date: 2008-07-04
forum: General Help
---

### Post by descentspb on 2008-07-04
I've installed a pptpd server on Ubuntu-server, and gave a pretty much default configuration to it. When i connect to it with the clients, they see the server perfectly, and the server itself sees them perfectly too. But the clients can not even ping each other with the adresses, that the VPN server gave them. How can I resolve it?

---

### Post by Gunman1982 on 2008-07-04
I don't know if if the server handles such stuff through forwarding those packages from one client to another. Try to activate it by executing the command on the server: 'sudo echo 1 > /proc/sys/net/ipv4/ip_forward' or if you are root anyway omit the sudo.

---

### Post by descentspb on 2008-07-04
Lots of thanks to u, mate!

---

