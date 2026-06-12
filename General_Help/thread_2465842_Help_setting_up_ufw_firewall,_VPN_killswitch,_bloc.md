---
title: "Help setting up ufw firewall, VPN killswitch, block non-VPN traffic"
date: 2021-08-12
forum: General Help
---

### Post by issh on 2021-08-12
Hello, 

Could someone help me set up UFW firewall so that it blocks all non-VPN traffic? My VPN is using the OpenVPN protocol. I am using a WiFi card and the device id is wlp4s0, not wlan0. I installed net-tools so that ifconfig works. I am following directions at this link, but it isn't working for me. [https://thetinhat.com/tutorials/misc/linux-vpn-drop-protection-firewall.html](https://thetinhat.com/tutorials/misc/linux-vpn-drop-protection-firewall.html)

I also found this script for UFW at this link: [https://askubuntu.com/questions/530088/ufw-for-openvpn](https://askubuntu.com/questions/530088/ufw-for-openvpn)
I don't understand this script very well. 

Also how to allow reconnect if the connection is lost: [https://askubuntu.com/questions/627622/ufw-vpn-how-to-allow-reconnection](https://askubuntu.com/questions/627622/ufw-vpn-how-to-allow-reconnection)

Here is the output from ifconfig: 

```
eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 78:2b:cb:a4:85:36  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xe1600000-e1620000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 9858  bytes 977111 (977.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9858  bytes 977111 (977.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.2.3.139  netmask 255.255.255.0  destination 10.2.3.139
        inet6 fe80::5f08:39a6:7210:f2e6  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 796  bytes 617052 (617.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 736  bytes 85511 (85.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet xxx.xxx.x.x  netmask 255.255.255.0  broadcast xxx.xxx.x.xxx
        inet6 fe80::f11a:641c:9b48:ca1f  prefixlen 64  scopeid 0x20<link>
        ether b8:ee:65:b2:61:19  txqueuelen 1000  (Ethernet)
        RX packets 847084  bytes 1196041170 (1.1 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 537272  bytes 63957293 (63.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

I redacted my ip address, I am using wlp4s0. So I assume that if I am following the directions at the link I listed above, then that is why ufw isn't working properly for me. 
What should I do to set up ufw correctly so that it blocks all non-VPN traffic? Also, would this interfere with setting up a VNC connection through TigerVNC or remote desktop connection through Remmina? I am going to need to connect to my Ubuntu PC through VNC or Remmina from my cell phone also. 

Regards.

---

### Post by TheFu on 2021-08-12
I've never done what you seek. Doubt ufw can accomplish it. iptables will probably be necessary.
Which release of Ubuntu is running and which "renderer" is being used to bring the VPN up?

ifconfig is deprecated. Use the 'ip' tools now.

---

