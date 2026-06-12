---
title: "Internet connection using firestarter not working"
date: 2007-10-18
forum: General Help
---

### Post by coolmanlg on 2007-10-18
I just installed ubuntu 7.04 and so far its cool. The only snag I have right now is with internet connection sharing.

I have installed firestarter and created policies to allow inbound connection on several ports for my LAN but computers on my LAN can't still browse. 

What am I doing wrong pls? 

the output of my iptables :

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.10.10.xxx               anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  10.10.10.xxx              anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
INBOUND    0    --  anywhere             192.168.0.44        
INBOUND    0    --  anywhere             10.0.12.xxx            
INBOUND    0    --  anywhere             192.168.0.255       
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   0    --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.0.12.xxx         10.10.10.xxx             tcp dpt:domain 
ACCEPT     udp  --  10.0.12.xxx              10.10.10.xxx              udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  192.168.0.148        anywhere            
ACCEPT     0    --  192.168.0.148        anywhere            
ACCEPT     0    --  192.168.0.13         anywhere            
ACCEPT     0    --  192.168.0.13         anywhere            
ACCEPT     0    --  192.168.0.13         anywhere            
ACCEPT     0    --  192.168.0.47         anywhere            
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:https 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:https 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpts:ftp-data:ftp 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpts:20:fsp 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:smtp 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:25 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:microsoft-ds 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8022 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8022 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8022 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8022 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
REJECT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
REJECT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST reject-with icmp-port-unreachable 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
REJECT     icmp --  anywhere             anywhere            icmp echo-request reject-with icmp-port-unreachable 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere         

Thanks

---

