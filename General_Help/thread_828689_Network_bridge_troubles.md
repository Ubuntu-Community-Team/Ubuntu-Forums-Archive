---
title: "Network bridge troubles"
date: 2008-06-14
forum: General Help
---

### Post by xravexheavenx on 2008-06-14
It seems I cannot get this network bridge working. It is going from the router, to wireless on computer a, through ethernet to computer b. I have edited my /etc/network/interfaces like many tutorials online with no luck and have used bride-utils directly to do it and cannot get it to work. Does anyone have any ideas?

---

### Post by iaculallad on 2008-06-14
> **xravexheavenx said:**
> It seems I cannot get this network bridge working. It is going from the router, to wireless on computer a, through ethernet to computer b. I have edited my /etc/network/interfaces like many tutorials online with no luck and have used bride-utils directly to do it and cannot get it to work. Does anyone have any ideas?

Try posting the ifconfig's for computer a and computer b.

---

### Post by DaDawn on 2008-06-14
> **iaculallad said:**
> Try posting the ifconfig's for computer a and computer b.

try sending ifconfig out put n just an example of how your /etc/network/interfaces looks like

---

### Post by xravexheavenx on 2008-06-14
Well, computer B at the moment is an xbox 360 but i plan to use DHCP so I can set up more than one adapter and run it to my mac as well.  here is the output of ifconfig on computer a:

br0       Link encap:Ethernet  HWaddr 00:16:01:3f:1e:35  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:1ff:fe3f:1e35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12241 (11.9 KB)  TX bytes:11202 (10.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:92:d2:43:1c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10902 (10.6 KB)  TX bytes:11521 (11.2 KB)
          Interrupt:221 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101316 (98.9 KB)  TX bytes:101316 (98.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:01:3f:1e:35  
          inet6 addr: fe80::216:1ff:fe3f:1e35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1392897 (1.3 MB)  TX bytes:44578 (43.5 KB)
          Interrupt:21 Memory:fdef8000-fdefc000


/etc/network/interfaces looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
iface br0 inet dhcp
bridge_ports wlan0 eth0
auto br0

---

### Post by cariboo on 2008-06-14
You may want to give arno-iptables-firewall a try. I used it for several years in my shop while I ran a computer repair service. I ran wirless from my home to the shop and had the server/gateway connected to an eight port switch. The firewall portion isn't really needed but it was there anyway. You used to have to set it up manually, but now I see there is a fairly nice setup script when you install it. It is available in the repositories and you can use Synaptic to install it.

Jim

---

### Post by iaculallad on 2008-06-14
Could you also post the IP address of your router.

---

### Post by xravexheavenx on 2008-06-14
Heh...  It seems I am getting errors even installing arno-iptables-firewall.

---

### Post by xravexheavenx on 2008-06-14
> **iaculallad said:**
> Could you also post the IP address of your router.

My router IP is 192.168.1.1

Just a standard Linksys WRT54G

---

### Post by gareth_005 on 2008-06-14
Here is my interfaces file:

I have 2 wired connections, eth0 and eth1.
I have also created 2 tunnel/tap interfaces, tap0 and tap1.
I only have one wired connection plugged in and I only use tap0, that is why they are the only 2 interfaces that are connected.

The bridge gets it's ip from my router with dhcp and it then assigns the other interface addresses automatically.

```

# The loopback network interface.
#
auto  lo
iface lo inet loopback

# Tap interfaces.
#
auto  tap0
iface tap0 inet ipv4ll
        tunctl_user gareth
auto  tap1
iface tap1 inet ipv4ll
        tunctl_user gareth

# The bridge.
#
auto  br0
iface br0 inet dhcp
        bridge_fd 0
        bridge_maxwait 0
        bridge_hello 0
        bridge_stp off
        bridge_ports eth0 tap0
        pre-up ip link set eth0 promisc on

```

Hope this helps a bit.

---

### Post by iaculallad on 2008-06-14
> **xravexheavenx said:**
> My router IP is 192.168.1.1

Just a standard Linksys WRT54G

Try putting static IP's on your configuration.

Say, Ethernet 0 of Computer A:

IP address: 192.168.2.1
Netmask: /24 or 255.255.255.0
Broadcast address: 192.168.2.255
Default Gateway: 192.168.1.1


For B (Xbox):

IP address: 192.168.2.2
Netmask: /24
Broadcast address: 192.168.2.255
Default Gateway: 192.168.2.1

Try placing your DNS address to your router's IP address.

---

### Post by xravexheavenx on 2008-06-14
Nope...  Still nothing.

Almost debating on just booting a router distro in one of these older boxes I have laying around.

---

### Post by cariboo on 2008-06-14
This may be a silly question, but why not just hook your other device to you router?

Jim

---

