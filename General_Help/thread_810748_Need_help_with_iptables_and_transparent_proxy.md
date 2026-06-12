---
title: "Need help with iptables and transparent proxy"
date: 2008-05-28
forum: General Help
---

### Post by modulok on 2008-05-28
I am moving an old squid server to a new squid server. Right now the squid server is also doing firewall (and transparent proxy is working fine).

The new setup will be two separate servers, squid/dansguardian and the other will be iptables/openvpn. I have the squid server working fine with my test client configured to proxy via the server. I need to get transparent proxy working to forward traffic through squid to the gateway server.

Legend:
internet = verizon dsl
gateway = firewall server
squid = proxy server

Network setup:
dsl internet = 192.168.1.1/24
gateway eth0 = 192.168.1.20/24
gateway eth1 = 10.2.2.99/16
squid eth1   = 10.2.2.100/16

squid's port is 3128
dansguardian's port is 8080

How do I go about this with the setup above?
Thanks

EDIT: I have tried this in iptables so far [via this link]("http://tldp.org/HOWTO/TransparentProxy-6.html"):
on gateway:

iptables -t nat -A PREROUTING -i eth1 -s ! 10.2.2.100 -p tcp --dport 80 -j DNAT --to 10.2.2.100:3128
iptables -t nat -A POSTROUTING -o eth0 -s 10.2.0.0/16 -d 10.2.2.100 -j SNAT --to 10.2.2.99
iptables -A FORWARD -s 10.2.0.0/16 -d 10.2.2.100 -i eth1 -o eth0 -p tcp --dport 3128 -j ACCEPT

---

### Post by modulok on 2008-05-29
bump, anyone have any ideas?

---

### Post by prshah on 2008-05-29
> **modulok said:**
> bump, anyone have any ideas?

Just a suggestion; in Hardy, there is a new supposedly easier interface to handle iptables, called ufw (uncomplicated firewall). Maybe you may find it easier to setup using that? I can't give any more details (out of my league) except ```
man ufw
``` but I hope it helps.

---

### Post by modulok on 2008-05-29
Thanks for the tip, but I have it almost working 100%.

Here are the commands for the firewall:> 
iptables -t nat -A PREROUTING -i eth1 -s ! 10.2.2.100 -p tcp --dport 80 -j DNAT --to 10.2.2.100:8080
iptables -t nat -A POSTROUTING -o eth1 -s 10.2.0.0/16 -d 10.2.2.100 -j SNAT --to 10.2.2.99
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth1 -j ACCEPT
iptables -A FORWARD -s 10.2.0.0/16 -d 10.2.2.100 -i eth1 -o eth1 -p tcp --dport 8080 -j ACCEPT


So at the moment, transparent proxy is working through DansGuardian and filtering like it should. The only thing that isn't working is ident. Ident is working if I manually enter the proxy server and port (squid:8080). 

> 1212084051.816    544 10.2.2.99 TCP_DENIED/403 0 GET [http://www.banned_site.com/](http://www.banned_site.com/) - DEFAULT_PARENT/127.0.0.1 text/html

1212084073.818    339 10.2.2.229 TCP_DENIED/403 0 GET [http://www.banned_site.com](http://www.banned_site.com) 'ident user' DEFAULT_PARENT/127.0.0.1 text/html


Does anyone know how to pass that information through the gateway so the DansGuardian logfile has the client IP and ident information about the user? Right now the access.log will only show one user, the gateway [10.2.2.99].

---

