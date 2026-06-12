---
title: "network-manager-openvpn kills internet connection but openvpn conf does not"
date: 2007-06-22
forum: General Help
---

### Post by harty83 on 2007-06-22
When I connect to my vpn server by running from a terminal:
```
sudo openvpn /etc/openvpn/bridge.conf
```

everything runs fine.  I have an internet connection and can communicate to my vpn server.

Here is the bridge.conf

```

client 
dev tap 
proto udp 
remote myserver.org 1194 
resolv-retry infinite 
nobind
persist-key 
persist-tun 
tls-client
ca /etc/openvpn/keys/myca.crt
cert /etc/openvpn/keys/mycrt.crt
key /etc/openvpn/keys/mykey.key
ns-cert-type server
tls-auth /etc/openvpn/keys/myta.key 1
cipher AES-128-CBC 
comp-lzo 
auth-user-pass

```

But when I connect via network-manager-vpn, I do not have an internet connection although I can communicate to the vpn server.  when I ps aux while connected via network-manager-opnevpn, I get the following:

```
/usr/sbin/openvpn --remote myserver.org --comp-lzo --nobind --dev tap --proto udp --port 1194 --cipher AES-128-CBC --tls-auth /etc/openvpn/keys/myta.key 1 --syslog nm-openvpn --up /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper --up-restart --persist-key --persist-tun --management 127.0.0.1 1194 --management-query-passwords --client --ns-cert-type server --ca /etc/openvpn/keys/myca.crt --cert /etc/openvpn/keys/mycrt.crt --key /etc/openvpn/keys/mykey.key --auth-user-pass

```

Any clue why I can browse the net with openvpn directly but not with network-manager-openvpn?

Thanks!
Alan

---

