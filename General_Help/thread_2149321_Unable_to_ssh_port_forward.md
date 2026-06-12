---
title: "Unable to ssh port forward"
date: 2013-05-28
forum: General Help
---

### Post by JaySeeJC on 2013-05-28
It seems i'm suddenly unable to port forward through my vps... Played around with some settings and now I have an extra interface and tons of headaches...

My interfaces:
```
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:395417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:395417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19991672 (19.9 MB)  TX bytes:19991672 (19.9 MB)


venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:750 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:133991 (133.9 KB)  TX bytes:79199 (79.1 KB)


venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:MYIPADDRESS  P-t-P:192.157.59.146  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1



```

Output of  nmap -p 1-65535 -T4 -A -v localhost:
```

Starting Nmap 5.21 ( http://nmap.org ) at 2013-05-28 18:42 MSK
NSE: Loaded 36 scripts for scanning.
Initiating Ping Scan at 18:42
Scanning localhost (127.0.0.1) [2 ports]
Completed Ping Scan at 18:42, 0.00s elapsed (1 total hosts)
Initiating Connect Scan at 18:42
Scanning localhost (127.0.0.1) [65535 ports]
Discovered open port 3306/tcp on 127.0.0.1
Discovered open port 587/tcp on 127.0.0.1
Discovered open port 25/tcp on 127.0.0.1
Discovered open port 22/tcp on 127.0.0.1
Discovered open port 80/tcp on 127.0.0.1
Discovered open port 53/tcp on 127.0.0.1
Discovered open port 443/tcp on 127.0.0.1
Discovered open port 25565/tcp on 127.0.0.1
Discovered open port 10000/tcp on 127.0.0.1
Discovered open port 953/tcp on 127.0.0.1
Completed Connect Scan at 18:42, 0.93s elapsed (65535 total ports)
Initiating Service scan at 18:42
Scanning 10 services on localhost (127.0.0.1)
etc...


```

Output of nmap -p 1-65535 -T4 -A -v serveraddress.com
```

Starting Nmap 5.21 ( http://nmap.org ) at 2013-05-28 18:43 MSK
NSE: Loaded 36 scripts for scanning.
Initiating Ping Scan at 18:43
Scanning jayseeofficial.com (MYIPADDRESS) [2 ports]
Completed Ping Scan at 18:43, 0.00s elapsed (1 total hosts)
Initiating Connect Scan at 18:43
Scanning jayseeofficial.com (MYIPADDRESS) [65535 ports]
Discovered open port 110/tcp on MYIPADDRESS
Discovered open port 80/tcp on MYIPADDRESS
Discovered open port 443/tcp on MYIPADDRESS
Discovered open port 22/tcp on MYIPADDRESS
Discovered open port 995/tcp on MYIPADDRESS
Discovered open port 53/tcp on MYIPADDRESS
Discovered open port 25/tcp on MYIPADDRESS
Discovered open port 10000/tcp on MYIPADDRESS
Discovered open port 465/tcp on MYIPADDRESS
Discovered open port 3535/tcp on MYIPADDRESS
Completed Connect Scan at 18:43, 0.92s elapsed (65535 total ports)
Initiating Service scan at 18:43
Scanning 10 services on jayseeofficial.com (MYIPADDRESS)
etc...

```

I'm currently learning to use some of the network diagnostic and configuration tools so any help there would be great too!

---

### Post by prodigy_ on 2013-05-28
Port forwarding *through* SSH is usually configured on the client side. Regular port forwarding should be done by the router. Neither requires adding new interfaces... unless in fact you want a secure *tunnel*. In case of the latter, SSH is a rather poor tool for the job because SSH uses TCP as its transport (you should look into VPN instead).

Long story short, start with explaining what exactly you're trying to achieve.

---

### Post by JaySeeJC on 2013-05-28
What I'm trying to achieve is forwarding the minecraft server on my laptop (port 25565) through my server. The command i'm currently using is ssh server.com -fR 25565:localhost:25565 sleep 30d
This has worked in the past, but I recently played around some settings on my vps provider's control panel and now can't forward. As mentioned above I used to have only one interface but now have two. I had enabled TUN/TAP and PPP but have since turned them both back off.

---

### Post by prodigy_ on 2013-05-28
Well, the ssh command looks OK (not sure about sleep - never used that). You can get rid of the :0 label easily:
```
ip addr del MYIPADDRESS/32 dev venet0
ip addr add MYIPADDRESS/<subnet prefix> dev venet0
```
But I doubt it'll help in any way. If you can reach your server, it's not an IP configuration issue.

Do you have a firewall on your server? If yes, you should check its settings.

---

