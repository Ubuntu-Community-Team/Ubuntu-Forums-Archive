---
title: "Site works from localhost, but from internet - timed out"
date: 2017-05-15
forum: General Help
---

### Post by van-oudshoorn on 2017-05-15
I run a webpage at /var/www/html/ on Ubuntu 16.04 that was working fine until today. Now I can connect to it from localhost, but not from the internet... I got timed out errors all the time. Please tell me how to find what's wrong?
Everything was working fine for nearly half a year, untill today. I haven't touched any configs of related recently. I don't have any router/firewall.

netstat -ntlp

[HTML]Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1468/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1304/smbd       
tcp        0      0 10.42.0.1:53            0.0.0.0:*               LISTEN      8496/dnsmasq    
tcp        0      0 10.42.1.1:53            0.0.0.0:*               LISTEN      1212/dnsmasq    
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1875/master     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1304/smbd       
tcp6       0      0 :::139                  :::*                    LISTEN      1304/smbd       
tcp6       0      0 :::80                   :::*                    LISTEN      1758/apache2    
tcp6       0      0 :::25                   :::*                    LISTEN      1875/master     
tcp6       0      0 0.0.0.0:25565           :::*                    LISTEN      6160/java       
tcp6       0      0 :::445                  :::*                    LISTEN      1304/smbd [/HTML]

iptables -L

[HTML]Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:bootps
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:bootps
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.0.0/24         state RELATED,ESTABLISHED
ACCEPT     all  --  10.42.0.0/24         anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
ACCEPT     all  --  anywhere             10.42.1.0/24         state RELATED,ESTABLISHED
ACCEPT     all  --  10.42.1.0/24         anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  [/HTML]
ufw is inactive

I searched posts with similar problems, maybe I need to flush iptable rules?

---

