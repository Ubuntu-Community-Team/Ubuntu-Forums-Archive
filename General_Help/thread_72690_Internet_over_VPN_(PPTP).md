---
title: "Internet over VPN (PPTP)"
date: 2005-10-07
forum: General Help
---

### Post by rene86 on 2005-10-07
A my University i can connect to internet via pptp. it isn't encrypted, so it should work on linux.
i can make i connection to the vpn-host, but linux doesn't route the internet data throught the pptp-connection. my local house-network has a dhcp and access to the university network, in this network is the vpn-server. i had to write a little script to not put the traffic for the vpn-server throught the vpn-connection. under windows it works great and the secret is right.
/etc/ppp/peers/uni:
```
pty "pptp vpn.uni-rostock.de --nolaunchpppd"
debug
user rm011
remotename PPTP
mtu 1492
nobsdcomp
noauth
lock
nodeflate
ipparam uni
```

/etc/ppp/ip-up.d/uni
```
#!/bin/sh

/sbin/route add -host 139.30.252.225 eth0
/sbin/route add -net 10.0.0.0/0 eth0
/sbin/route add -net 0.0.0.0/0 $PPP_IFACE
```

---

### Post by fabiand on 2005-10-07
Tag,

try:
/etc/ppp/peers/uni:
```

...
ipparam uni 172.20.0.1:172.20.0.2
```

/etc/ppp/ip-up.d/uni
```

route add default gw 172.20.0.2
```

Oh, and have a look at your /etc/resolv.conf

- fabiand

---

### Post by rene86 on 2005-10-08
It doesn't run.

My House-Network (10.x.x.x) has via an gateway access to the university-network (139.x.x.x).
The university-network is connected to the internet, but my house-network can't reach it. So I have to connect to an vpn-server in the university-network to be direct connected to the university-network and the internet.
my dns is in he university-network and works fine.

---

