---
title: "UfW dont deny ip blocks"
date: 2024-04-17
forum: General Help
---

### Post by 2000backups on 2024-04-17
Hi!
I have a webshop and for the moment it is the target for different spambots that create fake accounts. I can see on the ip address that they all come from a small number of well known abuse ip addresses. I block them in UFW but it seems that they are not blocked, because they concinue coming

This is my ufw status

80/tcp                     ALLOW       Anywhere                  
443                        ALLOW       Anywhere                  
22/tcp                     ALLOW       Anywhere                  
10000                      ALLOW       Anywhere                  
25                         ALLOW       Anywhere                  
Anywhere                   DENY        185.60.0.0/16             
Anywhere                   DENY        176.123.0.0/16            
Anywhere                   DENY        45.86.86.0/24             
Anywhere                   DENY        213.232.0.0/16            
Anywhere                   DENY        37.221.65.103             
143,465,587,993/tcp        ALLOW       Anywhere                  
Anywhere                   DENY        85.239.34.81       

What do I do wrong

TIA
Anders

---

### Post by The Cog on 2024-04-17
iptables and nftables parse the rules in order until they find a match, then do whatever that rule says. I *assume* that ufw does the same. So the higher rules in the list have higher precedence. In which case, any of those port numbers is allowed, and for those ports the DENY rule is never reached.
Try putting all the more specific DENY entries above the more general ALLOW entries.

---

