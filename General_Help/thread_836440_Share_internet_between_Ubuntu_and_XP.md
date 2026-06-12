---
title: "Share internet between Ubuntu and XP"
date: 2008-06-21
forum: General Help
---

### Post by mishathegoat on 2008-06-21
Hey everyone,

I was wondering if there was an easy way to share an internet connection between Ubuntu and Windows XP. I Googled but didn't find much help.. Could FireStarter help with this?

Any help is appreciated..

Thanks,
Misha the Goat

---

### Post by nikgare on 2008-06-21
Firestarter is what you want.
1st you get your machines cabled up so that they can see each other, then run firestarter and tell it the wan network port and the lan network port - that's just about all there is to it!

---

### Post by mishathegoat on 2008-06-21
Hmmm..

Whenever I try to start the "Start Firewall" I get an error that reads..

```
Failed to start the firewall

The device wifi0 is not ready.

Please check your network device settings and make sure your internet connection is active
```

Any ideas?

---

### Post by nikgare on 2008-06-22
Are you using wifi0 as your internet connected device?
What options does the wizard give you for this?

---

### Post by cariboo on 2008-06-22
First we need some basic information. Are these two seperate computers or is XP and Ubuntu on the same computer. If they are two seperate computers the easy way is to use a router. The hard way is to install a second nic in one of the copmputers. If XP and Ubuntu are on the same computer the answer is no.

Jim

---

### Post by mishathegoat on 2008-06-23
> **cariboo907 said:**
> First we need some basic information. Are these two seperate computers or is XP and Ubuntu on the same computer. If they are two seperate computers the easy way is to use a router. The hard way is to install a second nic in one of the copmputers. If XP and Ubuntu are on the same computer the answer is no.

Jim

Nope they are on separate computers.. and I could easily install another nic (which I'd probably prefer).

(also I'm using wifi0 to connect to the internet)

---

### Post by nikgare on 2008-06-23
Please post the output of ifconfig

---

### Post by mishathegoat on 2008-06-23
Maybe it's because the network manager is using it is the problem? I still don't know. Anywho here's my ifconfig

```
ath0      Link encap:Ethernet  HWaddr 00:0D:88:C7:07:A3  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fec7:7a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6737 errors:1 dropped:0 overruns:0 frame:0
          TX packets:4114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9369539 (8.9 MB)  TX bytes:386007 (376.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:07:E9:EE:56:1E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5609 (5.4 KB)  TX bytes:5609 (5.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0D-88-C7-07-A3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20664 errors:0 dropped:0 overruns:0 frame:4400
          TX packets:4327 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:11351497 (10.8 MB)  TX bytes:570017 (556.6 KB)
          Interrupt:18 

```

---

### Post by molotov00 on 2008-06-23
hold up. we do need more info. i used to do this:

one modem plugged into computer via usb. one network cable to switch then to another computer. i did 'internet connection sharing' inside xp. no two nics, no router. in this case my xp box bridged eth0 and a usb modem.

of course i hated that set up because if my xp box crashed/rebooted i lost internet. i only did it because it was temporary and cheap.

provide more info. 

or get a router or modem/router combo. this is by far the more practical solution and is actually more secure because you're also adding a hardware firewall (all decent routers have one). then you just run a cable from the router/modem to each of the computers. no messing in any os... just plug in a cable.

---

### Post by nikgare on 2008-06-24
The internet network device is ath0, not wifi0!
Try using **ath0** in the firestarter wizard.

Nik

---

