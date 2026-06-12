---
title: "Problem setting up a VPN server on Ubuntu 12.04"
date: 2013-07-20
forum: General Help
---

### Post by Ecoste on 2013-07-20
[COLOR=#000000][FONT=Verdana]Hello there, I recently bought a Linode vps for an IRC bot and I thought why not set-up a VPN server on it for the hell of it. Anyways, I followed this guide[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][http://silverlinux.blogspot.com/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html](http://silverlinux.blogspot.com/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Everything works fine, except that the VPS doesn't forward my packets to the internet. I double checked to make sure that I changed all of the text in the config files. I have also restarted the VPN after doing everything in the guide.[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Verdana]C:\Users\Pol>tracert google.com[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Tracing route to google.com [173.194.70.102] over a maximum of 30 hops:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1 45 ms 45 ms 45 ms 10.99.99.99 2 * * * Request timed out. 3 * * * Request timed out.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]And here's the ifconfig on the VPN.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]root@localhost:~# ifconfig eth0 Link encap:Ethernet HWaddr f2:3c:91:69:33:b2 inet addr:109.74.192.198 Bcast:109.74.192.255 Mask:255.255.255.0 inet6 addr: fe80::f03c:91ff:fe69:33b2/64 Scope:Link inet6 addr: 2a01:7e00::f03c:91ff:fe69:33b2/64 Scope:Global UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:12517 errors:0 dropped:0 overruns:0 frame:0 TX packets:1354 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:1308091 (1.3 MB) TX bytes:166456 (166.4 KB) Interrupt:76[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]lo Link encap:Local Loopback inet addr:127.0.0.1 Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:65536 Metric:1 RX packets:5 errors:0 dropped:0 overruns:0 frame:0 TX packets:5 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:90 (90.0 B) TX bytes:90 (90.0 B)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ppp0 Link encap:Point-to-Point Protocol inet addr:10.99.99.99 P-t-P:10.99.99.100 Mask:255.255.255.255 UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1396 Metric:1 RX packets:137 errors:0 dropped:0 overruns:0 frame:0 TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:3 RX bytes:19952 (19.9 KB) TX bytes:98 (98.0 B)[/FONT][/COLOR]

```[COLOR=#000000][FONT=Verdana]I'm not that experienced in networking so I have no idea what the issue is and how to fix it, pls halp.[/FONT][/COLOR]

---

### Post by Cheesemill on 2013-07-20
I would recommend using OpenVPN instead of PPTP as PPTP isn't secure.
Instructions can be found in the official Ubuntu documentation...
[https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

---

