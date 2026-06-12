---
title: "IRC Chat via OpenVPN"
date: 2017-03-25
forum: General Help
---

### Post by rawl747 on 2017-03-25
I am running OpenVPN on Ubuntu 14.04 LTS (client version) and wish to route my IRC Chat traffic through the VPN tunnel for anonymity.  In my qBittorent client, I can set the advanced configuration to only use the tun0 Network Interface which corresponds to the VPN tunnel connection.  Is there a way to configure the Ubuntu Hexchat IRC Chat client to use this VPN tunnel network connection and ONLY THIS VPN connection or is there a better IRC Chat client that will support this configuration?

Thanks!
rawl747

---

### Post by TheFu on 2017-03-25
Welcome to the forums.  

Usually, openvpn is setup as the default WAN route, so all traffic that leaves your LAN network would go over the VPN.  The most common exception is DNS, since many LANs have a separate DNS or caching-DNS server.  Use of the VPN is not on a per-application setup. It is a system-wide setting.

For example:

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.82.10.9      128.0.0.0       UG    0      0        0 tun0
default         rt1             0.0.0.0         UG    5      0        0 eth0
10.82.10.1      10.82.10.9      255.255.255.255 UGH   0      0        0 tun0
10.82.10.9      *               255.255.255.255 UH    0      0        0 tun0
108.61.101.140  rt1             255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.82.10.9      128.0.0.0       UG    0      0        0 tun0
172.22.22.0     *               255.255.255.0   U     0      0        0 eth0
```

My LAN is 172.x.x.x.
The VPN goes over 10.82.10.9 - and because the "metric" is less than my normal router (rt1), all external traffic goes out over tun0 (via 10.82.10.9) at the moment.

But because my LAN DNS is on a different machine, all my DNS requests are currently leaking. I need to fix that when/if my ISP starts selling my connection data.

Make sense?

If you aren't certain, post your **route** and **/etc/resolv.conf** to get more detailed help.

---

### Post by SeijiSensei on 2017-03-26
What about a simple routing solution?

Suppose your client has a VPN address of 10.10.10.10 and the other end of the tunnel has address 10.10.10.11.  Let the address of the IRC server be 192.168.168.168.  Then you can try
```
sudo ip route add 192.168.168.168 via 10.10.10.11
```
That should forward traffic for 192.168.168.168 out over the tunnel to 10.10.10.11.

---

