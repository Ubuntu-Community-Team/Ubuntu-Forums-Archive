---
title: "Strange networking issue."
date: 2013-05-31
forum: General Help
---

### Post by am_i_registered on 2013-05-31
Hello,

I'm experiencing a strange networking issue.
I'll try to provide as many information as possible...
I have a motherboard (ASUS P5E-WS Professional) with two ethernet cards (onboard) eth1 and eth2.
I have a VDSL router and I have connected its LAN1 port to eth1.
I want to enable Internet connection sharing in order to connect a second PC to the Internet and thus I have connected the 2nd PC to eth2.
The problem is that eth2 is not recognized by the system.
If I swap the cables, I get Internet through eth2 but then eth1 is not recognized!

```

root@P5E-WS:/home/am_i_registered# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:8c:5c:bc:cb  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe5c:bccb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50935125 (50.9 MB)  TX bytes:116321777 (116.3 MB)
          Interrupt:19 

eth2      Link encap:Ethernet  HWaddr 00:1e:8c:5c:bc:35  
          inet6 addr: fe80::21e:8cff:fe5c:bc35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:75943 (75.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:190549 (190.5 KB)  TX bytes:190549 (190.5 KB)

```

Both ethernet cards seem to work properly, but one is connected to the internet the other one is not recognizable!

Firestarter gives this message:
> 
Failed to start the firewall

The device eth2 is not ready.

Please check your network device settings and make sure your Internet connection is active.


When I'm trying to start the device from the terminal, I get the following:
```

root@P5E-WS:/home/am_i_registered# ifup eth2
Ignoring unknown interface eth2=eth2.

```

Any ideas?

---

### Post by plucky on 2013-05-31
Are you using an ethernet crossover cable to connect the two PC's?

Unless your ethernet cards are from Gigabyte,you will need a crossover cable to make it work.
You cannot connect two ethernet cards to each other and expect them to communicate.
Does your router have more than one rj45 sockets?

What is the make and model for your router?

---

### Post by am_i_registered on 2013-05-31
> **plucky said:**
> Are you using an ethernet crossover cable to connect the two PC's?

Unless your ethernet cards are from Gigabyte,you will need a crossover cable to make it work.
You cannot connect two ethernet cards to each other and expect them to communicate.
Does your router have more than one rj45 sockets?

What is the make and model for your router?

Yes, the cable that connects eth2 with the second PC is crossover.

The VDSL router is a ZTE router... I have to check for the exact model.. and yes it has 4 LAN ports... however my PCs are too far away and I have only one cable passed through the walls... if you are implying that I could connect the second PC directly to that router...

The problem here is not just the ICS is not working but the fact that the system cannot communicate with the second ethernet cards whenever the other card is connected to the Internet!

---

### Post by sanderj on 2013-05-31
You really should use the VDSL router as a router and connect both PCs to it. It will take care of everything, and it will avoid difficult configurations problems like you describe.

Your setup is now:
```
phonecable -- VDSLrouter ____ PC1 ____________________PC2
```

----- is twisted telefone cable
____ is ethernet cable

You should (and can) change it to:

```

phonecable ---------------- VDSLrouter ___ PC1
                                 |_________________________________PC2

```

HTH

---

### Post by am_i_registered on 2013-06-01
I know that the best solution would be to connect the second PC to the router directly... but there is a reason I can't do that..
The PC1 is connect to the wireless VDSL router with a cable on the router's LAN1 port due to the fact that the router is located in the living room and my room is too far and away the router wireless range.
The cable that travels from the living to my room is passed through the walls and this is done in way that the cable is not visible... getting a second cable to my room is too much of a hassle... that's way I wanted the ICS!

I have also a WLAN router... but when I connect the LAN cable that comes from the VDSL router to the WLAN router it does not work... no Internet. I don't know if there are any special setting needed for the WLAN... if it was working I would basically extended the range of the VDSL router and it would nice...

---

### Post by scbingham on 2013-06-01
You should be able to connect a second wireless router to your vdsl router.
Make sure the cable that comes into your room plugs into the socket labelled internet.
You will also need to turn dhcp off, as that is handled by the vdsl router.
I think you will probably have to choose another ssid name for the second router.

Hope this helps, try it & let us know.

---

### Post by pbrane on 2013-06-01
You need to setup the second wireless router (WLAN) as an access point, not a router. make sure its setup to use DHCP on the internet port so it will get an IP address from the VDSL router.

Have a look at this if you haven't already:  [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by scbingham on 2013-06-01
This article will be useful:

[http://compnetworking.about.com/od/routers/a/how-to-connect-two-routers-on-a-home-network.htm](http://compnetworking.about.com/od/routers/a/how-to-connect-two-routers-on-a-home-network.htm)

---

### Post by am_i_registered on 2013-06-01
Guys I can't get it to work! I officially resign :)
Thank you for your help!

---

### Post by bab1 on 2013-06-01
> **am_i_registered said:**
> Guys I can't get it to work! I officially resign :)
Thank you for your help!

The quick answer: Connect a switch to the cable going to the router and then connect both computers to that switch.

If your still interested I will explain why this works and ICS doesn't work.

---

### Post by am_i_registered on 2013-06-01
> **bab1 said:**
> The quick answer: Connect a switch to the cable going to the router and then connect both computers to that switch.

If your still interested I will explain why this works and ICS doesn't work.

I'm curious to know, please explain why if you can...

---

### Post by bab1 on 2013-06-01
The router you are using is actually 2 devices.  The ports are really attached to an internal switch.  That switch allows you to connect multiple devices that can communicate (through the routing device) with the Internet.  You may connect switches to other upstream switches as long as they are in the same network.  

An example of this is the following scenario:  You have a classroom with 4 tables, each with 4 computers.  Sixteen computers in all.  You have one router with only one port and a connection to the Internet.  How do we connect all of these devices?  One way (but not the best way) you could provide connectivity would be to provide 1 switch with 18 or more ports and connect the each computer and the router to the switch.

A MUCH BETTER way to do this would be to provide a 8 port switch for each table and a 8 port switch for the room.  Each table has its machines connected to a switch and and needs only 1 cable to connect to the room switch (many to one).  You then only need one cable to go between the room switch and the router's one port.  It makes no difference to the router whether all 16 computers are connected to 1 large switch or whether there are multiple switches connected together.  The switches, computers and router are all work together using Ethernet (a layer 2 protocol).   

When you use 2 network adapters (NIC) on one computer they are acting at TCI/IP (layer 3).  The TCP/IP protocol states that no device can have 2 NIC's operating in the same IP network.  One of those devices is always automatically turned off.  This is what you saw.

To configure ICS you need to configure your 2 NIC computer to be a router (or a bridge).  it's much simpler to use a cheap ($20) switch instead.  I have at home a router with only one Ethernet port for that network and a 4 port switch in a wiring closet.  One of the cables goes to the den where I have an 8 port switch to connect HTPC and other computers back to the router.

---

