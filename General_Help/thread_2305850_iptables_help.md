---
title: "iptables help"
date: 2015-12-09
forum: General Help
---

### Post by flashc5 on 2015-12-09
Can someone please tell me why this

```

#!/bin/bash

# forget old rules
iptables -F
iptables -X
iptables -Z

# set default policy to drop
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# allow loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# drop invalid packets
iptables -A INPUT  -m state --state INVALID -j DROP
iptables -A OUTPUT -m state --state INVALID -j DROP
iptables -A FORWARD -m state --state INVALID -j DROP

# allow established, related packets we've already seen
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# output chain
iptables -A OUTPUT -p tcp -m tcp --dport 53 -m comment --comment "DNS-TCP" -j ACCEPT
iptables -A OUTPUT -p udp -m udp --dport 53 -m comment --comment "DNS-UDP" -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 80 -m comment --comment "HTTP" -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 443 -m comment --comment "HTTPS" -j ACCEPT

```

creates this 

```

iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
[COLOR=#ff0000]**ACCEPT     all  --  anywhere             anywhere         **[/COLOR]   
DROP       all  --  anywhere             anywhere             state INVALID
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere             state INVALID

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
**[COLOR=#ff0000]ACCEPT     all  --  anywhere             anywhere          [/COLOR]**  
DROP       all  --  anywhere             anywhere             state INVALID
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain /* DNS-TCP */
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain /* DNS-UDP */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http /* HTTP */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https /* HTTPS */

```

I dont see where my rules allow for "ACCEPT all anywhere to anywhere"

Can someone please help me understand this.

Thanks in advance!

---

### Post by Doug S on 2015-12-10
Those lines are your local interface lines, where you did allow all protocols from anywhere, on both the INPUT and OUTPUT chains.

Displaying your iptables rules set the way you are can be misleading. Try this instead:```
sudo iptables -v -x -n -L
```and you will observe the interface is listed also.

---

### Post by flashc5 on 2015-12-10
That makes sense.  Thanks alot!

---

