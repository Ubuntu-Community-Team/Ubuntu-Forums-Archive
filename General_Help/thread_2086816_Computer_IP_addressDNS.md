---
title: "Computer IP address/DNS"
date: 2012-11-21
forum: General Help
---

### Post by Ragi1992 on 2012-11-21
I am trying to configure Mocha VNC Lite so I can use it as a remote desktop tool through my iPhone through Vino on my computer.

It wants the IP address or PC/Mac name
As well as the Server Port.

How do I find this information on Lubuntu?

I am running Lubuntu 12.04

---

### Post by papibe on 2012-11-21
Hi Ragi1992.

I'm not familiar with Mocha VNC Lite, but in order to get your IP address open a terminal and run:
```
ifconfig
```
The result should look something like:
```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:40:39:e1  
          inet addr:[COLOR="Red"]**192.168.1.101**[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe40:39e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:160807457 (160.8 MB)  TX bytes:21814069 (21.8 MB)
          Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:171848 (171.8 KB)  TX bytes:171848 (171.8 KB)

```
For the computer name:
```
hostname
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Ragi1992 on 2012-11-22
It keeps asking for a "Server Port"

It says default is 5900. Anybody know how to view your server port number?

---

### Post by papibe on 2012-11-22
You could use 'netstat'.

For instance, I'm running vino (default VNC service on Ubuntu 10.04):
```
netstat -lnptu | grep -i vino
```
The result looks like this:
```
tcp        0      0 127.0.0.1:**[COLOR="Red"]5900[/COLOR]**          0.0.0.0:*               LISTEN      1568/vino-server
tcp6       0      0 ::1:5900                :::*                    LISTEN      1568/vino-server

```
Which it seems to be using 5900, BTW.

Regards.

---

### Post by Ragi1992 on 2012-11-22
Nevermind forget it. The amount of work this OS puts you through for something as small as this is ridiculous. I just am not going to waste my time on something as stupid as this. Thanks for the help though.

---

### Post by Ragi1992 on 2012-11-22
Bump?

---

### Post by dcstar on 2012-11-22
> **Ragi1992 said:**
> Bump?

You complain that you are "not going to waste your time" and then bump the thread. Make your mind up.

If you want external access to your desktop then read the various HOWTOs that have existed for years on how to set it up.

**You** need to set up **your** router for port forwarding, **you** need to simply go to any of the "whatismyip" web sites to find out your public IP address. **You** need to figure out if you have a Static or Dynamic IP address.

---

