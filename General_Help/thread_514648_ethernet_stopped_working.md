---
title: "ethernet stopped working"
date: 2007-08-01
forum: General Help
---

### Post by sarahsilverman on 2007-08-01
okay, i needed a lot of extra space on ubuntu. i deleted many programs, i think i might have deleted something i need for ethernet. right now, i only can access internet through the live disc. so there must be something wrong with the operating system, not the modem or whatever.

my ethernet is : Broadcom 440x 10/100 integrated controller

i am running a regular dell inspiron 700m

thank you any help is greatly greatly appreciated :popcorn:

******************************************RSOLVED************************************************

---

### Post by aquavitae on 2007-08-01
How do you access the internet - Through a network or directly?  If its through a local network, can you access the network?  What happens if you open a terminal and type ```
ifconfig
```

---

### Post by sarahsilverman on 2007-08-01
> **aquavitae said:**
> How do you access the internet - Through a network or directly?  If its through a local network, can you access the network?  What happens if you open a terminal and type ```
ifconfig
```

i access directly from a modem, i will get right too you after i get off and on the live disc.:popcorn:

---

### Post by sarahsilverman on 2007-08-01
this is the output of "ifconfig" for the ubuntu installed

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:B0:80:7F  
          inet addr:66.91.170.8  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::20f:1fff:feb0:807f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71150 (69.4 KiB)  TX bytes:7914 (7.7 KiB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:66.91.168.1  Bcast:66.91.175.255  Mask:255.255.248.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.82.1  Bcast:192.168.82.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

this is for the live disc:

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:B0:80:7F  
          inet addr:66.91.170.8  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::20f:1fff:feb0:807f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1763438 (1.6 MiB)  TX bytes:191772 (187.2 KiB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by aquavitae on 2007-08-01
> **sarahsilverman said:**
> i will get right too you after i get off and on the live disc.:popcorn:Not sure if I understand right, but make sure you type ifconfig from your system, not the livecd.

---

### Post by aquavitae on 2007-08-01
Sorry - only saw your reply after my post!

Any idea what these are?
> **sarahsilverman said:**
> 
vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:66.91.168.1  Bcast:66.91.175.255  Mask:255.255.248.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.82.1  Bcast:192.168.82.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


The lo device is a loopback "virtual" device, but I think eth0 is the one you're interested in.  It looks fine here, so the device is working.  I assume then that the prblem is in the setup.  Btw have you tried pinging the internet: ```
ping www.google.com
```
Compare the file /etc/network/interfaces with the one on the live cd.  I'm not on linux right now, so I'm not sure if I have the path right - it might be something like /etc/net/interfaces or /etc/networking/interfaces.  Hunt around.

---

### Post by sarahsilverman on 2007-08-01
the output of the installed ubuntu is: ping: unknown host [www.google.com](www.google.com)

live cd is:

64 bytes from po-in-f103.google.com (72.14.253.103): icmp_seq=1 ttl=241 time=111 ms
64 bytes from po-in-f103.google.com (72.14.253.103): icmp_seq=2 ttl=241 time=106 ms
64 bytes from po-in-f103.google.com (72.14.253.103): icmp_seq=3 ttl=241 time=113 ms
64 bytes from po-in-f103.google.com (72.14.253.103): icmp_seq=4 ttl=241 time=114 ms
 and keeps on going

:confused:

---

### Post by Shib on 2007-08-01
what does

```
sudo cat /etc/resolv.conf
```

give you?

---

### Post by sarahsilverman on 2007-08-01
the interfaces file of the installed ubuntu is "

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


live cd is:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by sarahsilverman on 2007-08-01
> **Shib said:**
> what does

```
sudo cat /etc/resolv.conf
```

give you?

# generated by NetworkManager, do not edit!

search hawaii.rr.com


nameserver 66.75.164.90
nameserver 66.75.164.89

---

### Post by Shib on 2007-08-01
can you ping those IPs?

also, what's the output from "sudo route -n"?

---

### Post by sarahsilverman on 2007-08-01
i can't ping the ip adresses i get :

jonathan@jonathan-laptop:~$ ping 66.75.164.90
connect: Network is unreachable
jonathan@jonathan-laptop:~$ ping 66.75.164.89
connect: Network is unreachable
jonathan@jonathan-laptop:~$ 

this is the output of the "sudo route -n":

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.82.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
66.91.168.0     0.0.0.0         255.255.248.0   U     0      0        0 vmnet1
66.91.168.0     0.0.0.0         255.255.248.0   U     0      0        0 eth0


i see that is has something to do with vmware. you see, installed vmware server so i could make use of its virtualization. it asked me what ip to use and i put my own ip. is there anyway to reverse this, i mean if this is the problem?

thank you guys very much for staying with me, i really appreciate it :popcorn:

---

### Post by Shib on 2007-08-01
yah I'd say that vmware screwed up your networking stuff... try reinstalling it and giving it a 192.168.1.x address or something like that (10.x.x.x is fine too)

but, to fix your problem... if my subnetting is correct here, you should be able to do

```
sudo route add default gw 66.91.170.9
```

and things should... might... maybe if we're lucky work :)

---

### Post by aquavitae on 2007-08-01
> **sarahsilverman said:**
> # generated by NetworkManager, do not edit!

search hawaii.rr.com


nameserver 66.75.164.90
nameserver 66.75.164.89Is this on your system or the live cd?  What does the other one say?

---

### Post by sarahsilverman on 2007-08-01
> **Shib said:**
> yah I'd say that vmware screwed up your networking stuff... try reinstalling it and giving it a 192.168.1.x address or something like that (10.x.x.x is fine too)

but, to fix your problem... if my subnetting is correct here, you should be able to do

```
sudo route add default gw 66.91.170.9
```

and things should... might... maybe if we're lucky work :)

oh thank you thank you thank you, i am now posting form my installed ubuntu. i thank you all for helping me i really appreciate it a lot.

:guitar::KS:popcorn::):popcorn::KS:guitar:

---

### Post by sarahsilverman on 2007-08-01
> **aquavitae said:**
> Is this on your system or the live cd?  What does the other one say?

Thank you too, you were a really great help

you both rock for staying here and helping me ;)

:guitar::KS:guitar::KS:guitar:

---

### Post by Shib on 2007-08-01
yay! :D

(you might have to do that when you restart vmware as well if it's still misconfigured to screw with the network... but that's awesome that it's working for you!)

---

### Post by aquavitae on 2007-08-01
> **sarahsilverman said:**
> Thank you too, you were a really great help

you both rock for staying here and helping me ;)

:guitar::KS:guitar::KS:guitar:No prob.  Glad you got it working!

---

