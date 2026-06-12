---
title: "dnsmasq vs network-manager"
date: 2013-06-28
forum: General Help
---

### Post by ahardy66 on 2013-06-28
Just done an upgrade from 12.10 or so to raring ringtail 13.04 and I have a bunch of questions but I'll start with the bottleneck issue:

What could be interfering with my stand-alone dnsmasq config apart from the old culprit from the 12.04 upgrade? The upgrade re-installed network-manager and resolvconf which took over dnsmasq so I thought, "been there done that" and thought I'd solve it by removing the packages for network-manager and resolvconf. My machine is a gateway machine for the LAN with the modem on one NIC and the LAN on the other so I don't need the ubuntu desktop-oriented network-manager or resolvconf config. 

This time though, there is still something blocking dnsmasq - I have reconfigured it after the upgrade so that it reads my original /etc/dnsmasq.conf and /etc/resolv.conf but it doesn't want to co-operate. The gateway box is connected fine, but nothing can connect to the gateway via dhcp, despite the fact that dnsmasq is bound to the ports and looks like it's running alright.

Sorry I can't figure this one out, it seems I must have missed out some major point in my notes from last time, or there is something new that's been configured.

---

### Post by ahardy66 on 2013-06-29
Need to add a bit of info here. 

I said dnsmasq is bound to the ports but now I'm not sure. This is the output I get with netstat:

```

adam@gondor:~$ sudo netstat -nl46p|grep dnsmasq
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1203/dnsmasq    
tcp        0      0 192.168.0.3:53          0.0.0.0:*               LISTEN      1203/dnsmasq    
tcp6       0      0 ::1:53                  :::*                    LISTEN      1203/dnsmasq    
tcp6       0      0 fe80::2a37:37ff:fe03:53 :::*                    LISTEN      1203/dnsmasq    
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1203/dnsmasq    
udp        0      0 192.168.0.3:53          0.0.0.0:*                           1203/dnsmasq    
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1203/dnsmasq    
udp6       0      0 ::1:53                  :::*                                1203/dnsmasq    
udp6       0      0 fe80::2a37:37ff:fe03:53 :::*                                1203/dnsmasq    
adam@gondor:~$ 

```

but this is what I get from nmap when looking at the internal IP address of the gateway's 2nd nic:

```

adam@gondor:~$ nmap 192.168.0.3

Starting Nmap 6.00 ( http://nmap.org ) at 2013-06-29 16:42 BST
Nmap scan report for gondor.localdomain (192.168.0.3)
Host is up (0.00049s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
3689/tcp open  rendezvous
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.13 seconds
adam@gondor:~$

```

and this for UDP because DHCP is served via UDP:
```

adam@gondor:~$ sudo nmap -sU 192.168.0.3

Starting Nmap 6.00 ( http://nmap.org ) at 2013-06-29 16:53 BST
Nmap scan report for gondor.localdomain (192.168.0.3)
Host is up (0.000012s latency).
Not shown: 997 closed ports
PORT     STATE         SERVICE
53/udp   open          domain
68/udp   open|filtered dhcpc
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.25 seconds

```
which makes me think that actually, dnsmasq isn't running as it should. 

There is something on port 67 showing in the netstat result but I don't know how to interpret that, and dnsmasq doesn't show up on nmap. 

Does this provide any clues?

Thanks.

---

### Post by ahardy66 on 2013-06-30
by bizarre co-incidence, my lan hub decided to stop working at exactly the same time that I did the upgrade. Unfortunately I didn't see the little red light blinking because it was buried under a pile of wires and cables. I stopped and started it and, hey presto, issue solved.

---

### Post by gordintoronto on 2013-06-30
How to mark your thread as Solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

