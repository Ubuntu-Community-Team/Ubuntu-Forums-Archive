---
title: "Network Namespaces - how to connect namespace to physical network circumventing VPN"
date: 2016-01-02
forum: General Help
---

### Post by Davey_jones on 2016-01-02
I know nothing about *nix, just usage of google to learn what I can. What I'm trying to do is fairly simple and I think I am just missing something obvious. I have a machine running Ubuntu 14.04 that is connected to my VPN service provider with an openvpn connection. All traffic is routed through the VPN with this setup.

What I want to do is run Steam on this machine in its own namespace to connect directly to the internet without using the VPN connection. This is because in home streaming from my other machines obviously won't work if Steam connects over the VPN connection.

I am trying to do this with a network namespace. I've found plenty of examples of using the namespace to run the VPN within and using the namespace to just use certain programs with the VPN, but I want to have everything use the VPN and a namespace that does not use the VPN just for Steam.

I can create the network namespace and link it to the main network space easily. What I haven't figured out is how to provide external access to the internet for the namespace, I believe this is simple, and I'm also not certain how I'd connect the namespace to the internet avoiding the VPN operating in the main network space.

So far I've done this


> sudo ip netns add steam
sudo ip link add veth0 type veth peer name veth1
sudo ip link set veth1 netns steam
sudo ip netns exec steam ifconfig lo up
sudo ip netns exec steam ifconfig veth1 10.1.1.1/24 up
sudo ifconfig veth0 10.1.1.2/24 up


To get internet access to the namespace I've tried examples I've seen  using a bridge, which I failed miserably at resulting in no network  access on the machine at all, and others that suggest using iptables to  route internet traffic to the namespace.  I understand it revolves  around providing access to the veth0 virtual adapter in the main network  space so it can provide it to the linked veth1 in the steam namespace, I  just can't get it right.  I'm also not certain if/how I can do this  avoiding the active VPN in the main network space.


Here is what the network looks like without any of the steam network namespace modifications.



route -n results

> Kernel IP routing table
   
   
Destination----Gateway--------Genmask-------------Flags---Metric--Ref--Use--Iface

0.0.0.0 --------10.9.0.166------0.0.0.0---------------UG-------0------0-----0----tun0

10.9.0.1--------10.9.0.166------255.255.255.255----UGH-----0------0-----0----tun0

10.9.0.166------0.0.0.0--------255.255.255.255------UH------0-------0-----0----tun0

xx.xxx.xx.xx---192.168.1.1-----255.255.255.255----UGH-----0-------0-----0----eth0
^^^^^^=vpn external IP

192.168.1.0-----0.0.0.0---------255.255.255.0-------U------1-----0----0-----eth0                      




ifconfig results

> eth0      Link encap:Ethernet  HWaddr xx-xx-xx-xx-xx  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe4f:63f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3239090 errors:0 dropped:7 overruns:0 frame:0
          TX packets:6333617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:423243251 (423.2 MB)  TX bytes:8672067376 (8.6 GB)




lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:139214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172125088 (172.1 MB)  TX bytes:172125088 (172.1 MB)




tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.9.0.165  P-t-P:10.9.0.166  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1017279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1580136 errors:0 dropped:24937 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:208288016 (208.2 MB)  TX bytes:1375993303 (1.3 GB)                      




Thanks in advance.

---

