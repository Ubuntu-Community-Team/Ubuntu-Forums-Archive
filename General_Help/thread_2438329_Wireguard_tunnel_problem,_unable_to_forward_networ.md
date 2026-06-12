---
title: "Wireguard tunnel problem, unable to forward network outside the server"
date: 2020-03-10
forum: General Help
---

### Post by inzaghi89 on 2020-03-10
Hello,

yesterday I've tried to set up wireguard instead of openvpn. Almost all is ok... I can access my sever using the domain, and local address (10.0.0.1), but I can't access anything else. 

Server wg0.conf
```
[Interface]
Address = 10.0.0.1/24
PostUp = iptables -t nat -A POSTROUTING -o ens3 -j MASQUERADE; ip6tables -t nat -A POSTROUTING -o ens3 -j MASQUERADE
PostDown = iptables -t nat -D POSTROUTING -o ens3 -j MASQUERADE; ip6tables -t nat -D POSTROUTING -o ens3 -j MASQUERADE
ListenPort = 443
PrivateKey = private server key

[Peer]
PublicKey = public peer key
AllowedIPs = 10.0.0.2/32
```

Peer conf
```
[Interface]
PrivateKey = private peer key
Address = 10.0.0.2/32

[Peer]
PublicKey = public peer key
AllowedIPs = 0.0.0.0/0
Endpoint = server IP:443
PersistentKeepalive = 25
```

Ive enabled **net.ipv4.ip_forward=1**

---

### Post by TheFu on 2020-03-10
Did you setup the iptables rules to handle package forwarding to other subnets?

---

### Post by inzaghi89 on 2020-03-10
You're right... Will this solve an issue?
```
iptables -t nat -A POSTROUTING -o ens3 -j SNAT --to-source 123.456.789.12
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -j SNAT --to-source 123.456.789.12
iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 10.0.0.0/24 -j ACCEPT
iptables -A FORWARD -j REJECT
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o ens3
iptables -t nat -A POSTROUTING -j SNAT --to-source 123.456.789.12
```

---

