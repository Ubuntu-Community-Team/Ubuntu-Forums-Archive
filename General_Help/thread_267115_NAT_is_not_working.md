---
title: "NAT is not working"
date: 2006-09-28
forum: General Help
---

### Post by Aux on 2006-09-28
When I just installed Ubuntu, I've created my own script for starting NAT. It looks like that:

```
#! /bin/sh
EXTERNAL=eth1
INTERNAL=eth0
echo 1 > /proc/sys/net/ipv4/ip_forward
echo -n "Setting up NAT (Network Address Translation)..."
iptables -P FORWARD DROP
iptables -A FORWARD -i $EXTERNAL -o $INTERNAL -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $INTERNAL -o $EXTERNAL -j ACCEPT
iptables -t nat -A POSTROUTING -o $EXTERNAL -j MASQUERADE
iptables -A PREROUTING -t nat -p tcp -d 111.222.333.444 --dport 32460 -j DNAT --to 192.168.0.9
iptables -A PREROUTING -t nat -p udp -d 111.222.333.444 --dport 32460 -j DNAT --to 192.168.0.9
```

But after one of updates (as I remember Linux kernel was changed) my script is not working. iptables -L show:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (0 references)
target     prot opt source               destination

Chain PREROUTING (0 references)
target     prot opt source               destination
```

What is wrong and how to fix it? I'm kind of noobie...

---

