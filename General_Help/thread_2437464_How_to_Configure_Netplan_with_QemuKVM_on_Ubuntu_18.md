---
title: "How to Configure Netplan with Qemu/KVM on Ubuntu 18.04 Desktop?"
date: 2020-02-24
forum: General Help
---

### Post by mpugliesi2 on 2020-02-24
Hello everybody!

Let me try to explain as much as I can.

I am running Ubuntu 18.04.4 on my Laptop.  So, it's not a server and  No static IP! My internet connection is via WiFi, not by cable.

I need to keep my WiFi connection with QEMU/KVM running!

I managed to do that with Ubuntu 19.04, but with 18.04 and Netplan it is not working ! With 19.04 I have used network interfaces and works, but that's not the case with 18.04.  

How to configure Netplan and keep my WiFi connection?  

I just found outdated tutorials and always for servers with static IPs!!!!

Any solution for that?

Here is my ifconfig -a:

```
enp7s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether a4:1f:72:ff:9f:f0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3203  bytes 334686 (334.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3203  bytes 334686 (334.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.250.21.249  netmask 255.255.224.0  broadcast 10.250.31.255
        inet6 fe80::a48c:8e30:b748:6a98  prefixlen 64  scopeid 0x20<link>
        ether 54:35:30:fe:d9:01  txqueuelen 1000  (Ethernet)
        RX packets 200241  bytes 76868844 (76.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 33128  bytes 5210826 (5.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

And here is my netplan config file at the moment:



```
 cat /etc/netplan/1-network-manager-all.yaml 
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

---

### Post by TheFu on 2020-02-27
Nobody responded in 3 days.   

Google found this:
[https://unix.stackexchange.com/questions/118891/wireless-bridged-networking-in-kvm-why-is-it-so-complicated](https://unix.stackexchange.com/questions/118891/wireless-bridged-networking-in-kvm-why-is-it-so-complicated)

---

