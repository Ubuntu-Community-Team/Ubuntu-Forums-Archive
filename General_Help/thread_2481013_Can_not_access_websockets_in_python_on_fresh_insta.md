---
title: "Can not access websockets in python on fresh install of 22.04LTS"
date: 2022-11-16
forum: General Help
---

### Post by tmf1 on 2022-11-16
[COLOR=#000000]I install 22.04LTS fresh, and tried to run websockets server in Python, I can see the port is open but can never connect, UFW is disabled, the only thing I can think of is the routing table?? I am a little familiar with Linux, but would appreciate some help.

[/COLOR]The install is minimal, and no webserver setup.

[COLOR=#000000]I have the same code working on a CentOS machine, that already had a website running on it...[/COLOR]

[COLOR=#000000]Thanks!

In case this helps,
[/COLOR][COLOR=#24292F][FONT=-apple-system]the IP on the machine is 192.168.2.43[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         mynetwork       0.0.0.0         UG    100    0        0 eno1
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

```[/FONT][/COLOR]

---

### Post by The Cog on 2022-11-16
What port? 
Where are you trying to connect from?
How do you know it fails to connect - how do you try to connect and what error message do you get?
Can you also run these commands while the socket server is listening and post the commands you typed and the results:
```
ss -lnt
ip addr
sudo iptables-save
sudo nft list ruleset
```

---

### Post by tmf1 on 2022-11-16
> What port?

55550 but I have also tried 8887 and 8889, same results

> Where are you trying to connect from?

I have tried from the internet through an open port on the router, have also tried on the same net as the server locally.

> How do you know it fails to connect - how do you try to connect and what error message do you get?

Just does not connect, but I do the exact same thing on my CentOS and get connections.

> Can you also run these commands while the socket server is listening and post the commands you typed and the results:

```
ss -lnt

State            Recv-Q           Send-Q                     Local Address:Port                     Peer Address:Port           Process
LISTEN           0                4096                       127.0.0.53%lo:53                            0.0.0.0:*
LISTEN           0                128                              0.0.0.0:22                            0.0.0.0:*
LISTEN           0                128                            127.0.0.1:631                           0.0.0.0:*
LISTEN           0                128                                 [::]:22                               [::]:*
LISTEN           0                128                                [::1]:631                              [::]:*
rick@rick-Precision-T3600:~$ ss -lnt
State            Recv-Q           Send-Q                     Local Address:Port                      Peer Address:Port          Process
LISTEN           0                4096                       127.0.0.53%lo:53                             0.0.0.0:*
LISTEN           0                128                              0.0.0.0:22                             0.0.0.0:*
LISTEN           0                128                            127.0.0.1:631                            0.0.0.0:*
LISTEN           0                5                                0.0.0.0:55550                          0.0.0.0:*
LISTEN           0                4096                                   *:43423                                *:*
LISTEN           0                4096                                   *:33601                                *:*
LISTEN           0                4096                                   *:39841                                *:*
LISTEN           0                4096                                   *:37449                                *:*
LISTEN           0                4096                                   *:46409                                *:*
LISTEN           0                4096                                   *:46473                                *:*
LISTEN           0                4096                                   *:38857                                *:*
LISTEN           0                4096                                   *:42027                                *:*
LISTEN           0                4096                                   *:43757                                *:*
LISTEN           0                4096                                   *:44849                                *:*
LISTEN           0                4096                                   *:63313                                *:*
LISTEN           0                4096                                   *:41233                                *:*
LISTEN           0                4096                                   *:50929                                *:*
LISTEN           0                4096                                   *:41941                                *:*
LISTEN           0                128                                 [::]:22                                [::]:*
LISTEN           0                4096                                   *:43895                                *:*
LISTEN           0                4096                                   *:41079                                *:*
LISTEN           0                128                                [::1]:631                               [::]:*
LISTEN           0                4096                                   *:45659                                *:*
LISTEN           0                4096                                   *:36797                                *:*


ip addr

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 18:03:73:3c:3f:04 brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.2.43/24 brd 192.168.2.255 scope global dynamic noprefixroute eno1
       valid_lft 258836sec preferred_lft 258836sec
    inet6 fe80::fdca:e3c8:789b:5463/64 scope link noprefixroute
       valid_lft forever preferred_lft forever


sudo iptables-save

nothing returned

sudo nft list ruleset

nothing returned

```

Thanks!

---

### Post by The Cog on 2022-11-17
That's all looking OK so far. I can see it's listening on all addresses port 55550. No firewall rules in play. 
Lots of other services listening, but I don't think they're relevant other than to ask are they working, or is the whole machine unreachable?
I don't like the look of gateway "mynetwork" in your routing table though.  Can you post the result of these 2 please, just in case it's significant:
```
ip ro
ip ro get 1.1.1.1
```
But I think we're probably into tracing packets to figure this out. Run this command and then try to connect to the service to print all the packets, and let's see what's happening on the network:
```
sudo tcpdump -nnl tcp port 55550
```
We'll see if the connect request arrives and if it is responded to.

And you still haven't said how you try to connect and how you know it fails to connect. Are you using a custom written client, or a web browser, or something else? Does it have a proxy configured? Does it say timeout, or connection refused, or something else?

---

### Post by tmf1 on 2022-11-17
> **The Cog said:**
> That's all looking OK so far. I can see it's listening on all addresses port 55550. No firewall rules in play. 
Lots of other services listening, but I don't think they're relevant other than to ask are they working, or is the whole machine unreachable?
I don't like the look of gateway "mynetwork" in your routing table though.  Can you post the result of these 2 please, just in case it's significant:
```
ip ro
ip ro get 1.1.1.1
```
But I think we're probably into tracing packets to figure this out. Run this command and then try to connect to the service to print all the packets, and let's see what's happening on the network:
```
sudo tcpdump -nnl tcp port 55550
```
We'll see if the connect request arrives and if it is responded to.

And you still haven't said how you try to connect and how you know it fails to connect. Are you using a custom written client, or a web browser, or something else? Does it have a proxy configured? Does it say timeout, or connection refused, or something else?

The other services are RAY instances that python spun up, they must use these to communicate process to process... 

mynetwork would have been something ubuntu added on install, as this is really a fresh install, nothing been done

```
rick@rick-Precision-T3600:~/models$ ip rodefault via 192.168.2.1 dev eno1 proto dhcp metric 100
169.254.0.0/16 dev eno1 scope link metric 1000
192.168.2.0/24 dev eno1 proto kernel scope link src 192.168.2.43 metric 100
rick@rick-Precision-T3600:~/models$ ip ro get 1.1.1.1
1.1.1.1 via 192.168.2.1 dev eno1 src 192.168.2.43 uid 1000
    cache

```

As for the tcpdump, it works if I access it from private IP 192.168.2.43, but not public IP.

The WIFI router connect to VDSL internet provider I opened port 55550 and pointed it to 192.168.2.43
When I run the python websocket server I can see the port open, if I exit the script the port closes.
Based on this it looks like the port forwarding is working.
I use this site to determine that: [https://www.whatismyip.com/port-scanner/](https://www.whatismyip.com/port-scanner/)

So the question remains why can they scan my port and it open or closed, yet I can not seem to open it ??
** edit I can also see their probing of open/close on the tcpdump

Thanks!

---

### Post by The Cog on 2022-11-18
> As for the tcpdump, it works if I access it from private IP 192.168.2.43, but not public IP.
What does that mean? tcpdump always works - no bugs that I'm aware of.
Do you mean that you don't see any packets printed when trying to connect from a public ip? If that's the case then no packets are reaching your server, and you need to look at the rest of the network and find out why not. tcpdump has the final say here - if tcpdump doesn't print a line for the incoming request packet, then it didn't arrive. 

You could perhaps remove the "tcp port 55550" filter to see if the connection is being redirected to a different port number, but then it'll print every packet seen which could be rather noisy. Maybe use "host x.x.x.x" as a filter instead, to only print packets to/from the public ip.

---

### Post by tmf1 on 2022-11-18
Yes not working as no packets....

Been playing and tcpdump is very useful.

Makes zero sense then why when I use [https://www.whatismyip.com/port-scanner/](https://www.whatismyip.com/port-scanner/) it works shows port open to the public IP, yet opening a websocket to the same public IP with same port, I see zero tcpdump activity!

](*,)

Richard.

[CENTER][COLOR=#000000]

[/COLOR][/CENTER]

---

