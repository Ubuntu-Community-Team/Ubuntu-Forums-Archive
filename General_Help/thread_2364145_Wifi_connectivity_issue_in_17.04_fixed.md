---
title: "Wifi connectivity issue in 17.04 fixed"
date: 2017-06-19
forum: General Help
---

### Post by castor_fou on 2017-06-19
Since 17.04 upgrade, I have experienced some wifi connectivity issues from time to time.
When the connection is established, it works. But from time to time it is difficult to get it : at boot time or at resume.

Here was an example of logs :

```
info>  [1497888417.0200] manager: NetworkManager state is now CONNECTED_GLOBAL
info>  [1497888417.0201] policy: set 'faidherbe5ghz' (wlan0) as default for IPv4 routing and DNS
info>  [1497888417.0205] device (wlan0): Activation: successful, device activated.
info>  [1497888417.1297] policy: set 'faidherbe5ghz' (wlan0) as default for IPv6 routing and DNS
info>  [1497890416.6990] manager: sleep requested (sleeping: no  enabled: yes)
info>  [1497890416.6991] manager: sleeping...
info>  [1497890416.6992] manager: NetworkManager state is now ASLEEP
info>  [1497890416.6998] device (wlan0): state change: activated -> deactivating (reason 'sleeping') [100 110 37]
info>  [1497890416.7133] device (wlan0): state change: deactivating -> disconnected (reason 'sleeping') [110 30 37]
info>  [1497890416.7477] dhcp4 (wlan0): canceled DHCP transaction, DHCP client pid 7624
info>  [1497890416.7477] dhcp4 (wlan0): state changed bound -> done
info>  [1497890416.7520] device (wlan0): set-hw-addr: set MAC address to CA:A3:EC:63:D5:50 (scanning)
warn>  [1497890416.7553] sup-iface[0x560695ca66c0,wlan0]: connection disconnected (reason -3)
```

I have understood from last line that it is an issue with dhcp timeout.

I have found someone explaining he has issues with internal dhcp management from NetworkManager.
I have moved from internal to dhclient, it has fixed my issue.

```
 cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile
dhcp=dhclient

[ifupdown]
managed=false
```

Hope it could help others.

---

