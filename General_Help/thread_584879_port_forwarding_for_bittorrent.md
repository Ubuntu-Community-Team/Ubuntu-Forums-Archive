---
title: "port forwarding for bittorrent"
date: 2007-10-21
forum: General Help
---

### Post by tatortot on 2007-10-21
I recently switched to Ubuntu and have loved it so far except for the fact I cant get my ports forwarded correctly in linux. My ports are already configured for my modem/NAT from when I was using windows. I have even tried disabling iptables but still no luck. (not sure if I did it correctly) Most of the forum post I've read gave instructions for either the terminal or firestarter and neither have worked for me so far. I know plenty of people are doing fine with torrents on linux, so it must be something I'm missing.

I know its stupid , but I would rather have no firewall than have to use windows for torrents.

BTW, I'm using Utorrent

Any help would be appreiciated.

---

### Post by por100pre1 on 2007-10-21
Which ports do you need to be open? Let's see what you got:

```
sudo iptables -L
```

post the results... 

Try [Deluge]("http://deluge-torrent.org/downloads"). If using Gutsy do this:

```
sudo aptitude install deluge-torrent
```

---

### Post by Rumo on 2007-10-21
> **tatortot said:**
>  My ports are already configured for my modem/NAT from when I was using windows. 
So you have configured your router to forward ports to your computer!? Now everything you need to do is tell your bittorrent client the correct ports. I don't know uTorrent but this should be pretty easy.

> **tatortot said:**
>  
I have even tried disabling iptables but still no luck. (not sure if I did it correctly)

You probably don't even need a firewall. After a fresh install there are no open ports on an ubuntu computer and even if your using ssh-server or some other sort of server application your system should be pretty safe. My desktop at my university office is online 24/7 with a static IP address, without a firewall and without rootkits or viruses (so far).

---

### Post by tatortot on 2007-10-21
> Which ports do you need to be open? Let's see what you got:
I use 54321 for bittorent

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dslrouter            anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dslrouter            anywhere            
ACCEPT     tcp  --  dslrouter            anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dslrouter            anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             localhost           
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  desktop              dslrouter           tcp dpt:domain 
ACCEPT     udp  --  desktop              dslrouter           udp dpt:domain 
ACCEPT     tcp  --  desktop              dslrouter           tcp dpt:domain 
ACCEPT     udp  --  desktop              dslrouter           udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             localhost           
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSO        tcp  --  anywhere             anywhere            tcp dpt:54321 
LSO        udp  --  anywhere             anywhere            udp dpt:54321 
ACCEPT     0    --  anywhere             anywhere            

```

> Try Deluge
I have deluge already installed and have the same problem. I've been using utorrent for some time and would rather not change unless it was necessary.

> So you have configured your router to forward ports to your computer!? Now everything you need to do is tell your bittorrent client the correct ports
Yes, my modem/nat is forwarding ports to the computer but Ubuntu is stoping the packets before they get to utorrent or any other bittorrent  client.
> You probably don't even need a firewall. After a fresh install there are no open ports on an ubuntu computer
When you install Ubuntu there is already a firewall built in and its the firewall that blocks all the ports.

---

### Post by Rumo on 2007-10-22
> **tatortot said:**
> 
When you install Ubuntu there is already a firewall built in and its the firewall that blocks all the ports.
Iptables is part of the linux kernel. But there are no rules defined on a standard ubuntu install.

---

