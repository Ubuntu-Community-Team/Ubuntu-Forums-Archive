---
title: "IPTABLE help please"
date: 2015-12-11
forum: General Help
---

### Post by davaweb on 2015-12-11
Hi,
Ubuntu 14.02.3

I'm having problems with setting up IPTABLES so all internet traffic is confined to my vpn. The .ovpn file is placed in /etc/openvpn and has the vpn ip addresses in it.

This is my IPTABLES before doing anything - standard for Ubuntu:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

The script I run is:
```
#!/bin/sh

# Set base policy to reject all Incoming traffic
sudo iptables -P INPUT DROP
#
# ALLOW loopback Incoming traffic for lan browsing
sudo iptables -A INPUT -i lo -j ACCEPT
#
# ALLOW incoming traffic associated with a connection
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
#
# ALLOW incoming traffic on eth0 (from LAN)
sudo iptables -A INPUT -i eth0 -s 192.168.1.0/24 -j ACCEPT
#
# ALLOW incoming traffic on eth0 (from LAN) if associated with a connection
sudo iptables -A OUTPUT -o eth0 -d 192.168.1.0/24 -m state --state RELATED,ESTABLISHED -j ACCEPT
#
# Not required as my IP address is always the same as the ovpn file when vpn is running.
# sudo iptables -A OUTPUT -p udp --sport 67 -j ACCEPT
#
# Parse ovpn files I use for vpn connections (they are in /etc/openvpn)
sudo grep -h '^remote ' /etc/openvpn/*.ovpn | /usr/bin/cut -d ' ' -f 2 | /usr/bin/sort -du | /usr/bin/xargs -I @ iptables -A OUTPUT -d @ -j ACCEPT
#
# REJECT all other OUTBOUND traffic on eth0. (If this rule is anywhere else OUTBOUND to the vpn connection would be blocked.
sudo iptables -A OUTPUT -o eth0 -j REJECT

```

IPTABLES after running this are:
```
~$ sudo iptables -L
[sudo] password for david: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
david@graphics140403G:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.1.0/24       anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.1.0/24       state RELATED,ESTABLISHED
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
```

I can neither browse the internet nor can I browse my LAN with or without the vpn running.

I would very much appreciate help - thank you.

---

