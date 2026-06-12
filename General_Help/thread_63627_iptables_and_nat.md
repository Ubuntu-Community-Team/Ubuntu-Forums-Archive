---
title: "iptables and nat?"
date: 2005-09-08
forum: General Help
---

### Post by cristianommxp on 2005-09-08
Hi, 

I'm using two computers:

PC A) Ubuntu Hoary

PC B) Windows 98, IP 192.168.0.5


The PC number A access internet and do NAT for pc number B.


Well, 

there are two situations here.

Situation number 1
-----------------------------------------------------------
sudo iptables -P FORWARD ACCEPT
sudo iptables -t nat -A POSTROUTING -s 192.168.0.5 -o wlan0 -j MASQUERADE
-----------------------------------------------------------

When I do the situation number 1, it's works all fine.

But, I have the situation number 2:

Situation number 2
-----------------------------------------------------------
# Drop connections
sudo iptables -P FORWARD DROP
# Open connections to web services
sudo iptables -A FORWARD -s 192.168.0.5 -p tcp --dport 80 -j ACCEPT
# Open connections to e-mail services
sudo iptables -A FORWARD -s 192.168.0.5 -p tcp --dport 25 -j ACCEPT
# Open connections to DNS server
sudo iptables -A FORWARD -s 192.168.0.5 -d 172.16.23.21 -j ACCEPT
# Doing NAT
sudo iptables -t nat -A POSTROUTING -s 192.168.0.5 -o wlan0 -j MASQUERADE
-----------------------------------------------------------

When I'm doing the situation number 2, I can't open web address in browser in PC B.

What's wrong?

10ks

Cristiano

---

### Post by KenLazlo on 2005-09-14
This configuration only forwards packets to the Internet, but not the other way - answer packets of internet servers to your win pc. 

It's a good idea to use the state directive. all related packets are allowed with this:

iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

---

