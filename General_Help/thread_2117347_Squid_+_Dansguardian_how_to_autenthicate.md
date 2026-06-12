---
title: "Squid + Dansguardian: how to autenthicate"
date: 2013-02-18
forum: General Help
---

### Post by demonide on 2013-02-18
Hi, 
I've got an Ubuntu Server 12.04 32b and I want to authenticate my squid users and enable Dansguardian's webfiltering. Squid3 authentication works fine on port 3128, Dansguardian's blacklists works only if I set port 8080 on my clients' browser but, in this way, I cannot authenticate any users.
Do you know a way to solve? These are my configurations:

**dansguardian.conf**
...
filterip = 192.168.0.1 # My proxy server
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128
...

**squid.conf**
...
visible_hostname localhost
auth_param basic program /usr/lib/squid3/ncsa_auth /etc/squid3/passwd
auth_param basic children 5
auth_param basic realm
auth_param basic credentialsttl 24 hours
...
http_port 3128

and **/etc/network/interfaces**
...
pre-up echo 1 > /proc/sys/net/ipv4/ip_forward
pre-up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
down iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
pre-up iptables -t nat -A OUTPUT -p tcp -m tcp --dport 80 -m owner ! --uid-owner proxy -j REDIRECT --to-ports 3128
pre-up iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128
...

Note: eth0 wan, eth1 lan.

Thank you very much.

---

