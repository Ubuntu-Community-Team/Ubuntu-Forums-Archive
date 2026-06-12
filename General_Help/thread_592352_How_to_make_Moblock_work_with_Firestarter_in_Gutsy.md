---
title: "How to make Moblock work with Firestarter in Gutsy?"
date: 2007-10-26
forum: General Help
---

### Post by chunchengch on 2007-10-26
I have Firestarter installed in Gutsy, and then I install Moblock, but the conflict between both causes my laptop failed to enter GDM, so I modify the file /etc/moblock/moblock.conf to let Firestarter control the iptable rules, I change the value of string [COLOR="Blue"]IPTABLES_SETTINGS="1"[/COLOR] from 1 to 0 and the value of string [COLOR="Blue"]IPTABLES_ACTIVATION="2"[/COLOR] from 2 to 0, then save the file and reboot laptop, now I think both Firestarter and Moblock work normally.

However, I am not very sure everything goes well, so I type command to check if Moblock is working or not, here is the output:

[COLOR="Red"]$ sudo moblock-control status [/COLOR]

[COLOR="Purple"]Current iptables rules (this may take awhile): 

Chain INPUT (policy DROP) 
target     prot opt source               destination         
ACCEPT     tcp  --  xxx.xxx.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  xxx.xxx.1.1          anywhere            
ACCEPT     tcp  --  ns1.xxxxx.net.tw    anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns1.xxxxx.net.tw    anywhere            
ACCEPT     tcp  --  ns2.xxxxx.net.tw    anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns2.xxxxx.net.tw    anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             xx.xx.xxx.255       
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
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
ACCEPT     tcp  --  xxxx.STATIC.xxxxx.net.tw  xxx.xxx.1.1         tcp dpt:domain 
ACCEPT     udp  --  xxxx.STATIC.xxxxx.net.tw  xxx.xxx.1.1         udp dpt:domain 
ACCEPT     tcp  --  xxxx.STATIC.xxxxx.net.tw  ns1.xxxxx.net.tw   tcp dpt:domain 
ACCEPT     udp  --  xxxx.STATIC.xxxxx.net.tw  ns1.xxxxx.net.tw   udp dpt:domain 
ACCEPT     tcp  --  xxxx.STATIC.xxxxx.net.tw  ns2.xxxxx.net.tw   tcp dpt:domain 
ACCEPT     udp  --  xxxx.STATIC.xxxxx.net.tw  ns2.xxxxx.net.tw   udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references) 
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4662 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4662 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5000 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5000 
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

Chain LSO (0 references) 
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references) 
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            

Please check if the above printed iptables rules are correct! 

 * moblock is running, pid is 5626.[/COLOR]


Now I know Moblock is running, the remaining question is that I am not really sure all these iptables rules above are correct, will anyone kindly check it for me? thanks a lot!

---

