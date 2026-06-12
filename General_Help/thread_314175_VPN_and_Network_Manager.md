---
title: "VPN and Network Manager"
date: 2006-12-07
forum: General Help
---

### Post by Bou on 2006-12-07
Hi, for some time I'be been using VPNC to connect to the Internet from my university, but I've noticed that the repos have a package that handles this kind of connections: network-manager-pptp.

Since I have no clue about configuring this kind of connections, could you give me a hand? This is my /etc/vpnc/default.conf, with all necessary data for the connection:

> IPSec gateway vpn-server.uji.es
IPSec ID UJI
IPSec secret xxxxxxxx
Xauth username xxxxxxxx

And these are the settings of the connection I created in network-manager-pptp:

> Description=UJI
Connection-Type=pptp
PPTP-Server=vpn-server.uji.es
Use-Peer-DNS=yes
Encrypt-MPPE=no
Encrypt-MPPE-128=yes
Compress-MPPC=no
Compress-Deflate=no
Compress-BSD=no
PPP-Lock=yes
Auth-Peer=no
Refuse-EAP=no
Refuse-CHAP=no
Refus*****HAP=no
MTU=1416
MRU=1416
LCP-Echo-Failure=10
LCP-Echo-Interval=10
PPP-Custom-Options=
Peer-DNS-Over-Tunnel=yes
X-NM-Routes=
Use-Routes=no

As you can see, I couldn't set most required data and I don't know what most offered options are, or if I should leave them checked or unchecked. Besides, NM doesn't allow me to connect to the created connection.

What should I do?

---

### Post by gunksta on 2006-12-07
The network-manager-pptp won't help you with vpnc connections. If you are using VPNC it is because you need to connect to a Cisco VPN server. nm-pptp helps you connect to a Microsoft VPN server.

If you look around on the forums for a package called network-manager-vpnc, you will get what you want.

--andy

---

