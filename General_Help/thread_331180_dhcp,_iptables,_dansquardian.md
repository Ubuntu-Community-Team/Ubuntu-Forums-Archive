---
title: "dhcp, iptables, dansquardian"
date: 2007-01-04
forum: General Help
---

### Post by christodoulos77 on 2007-01-04
Hello there

I have a strange problem
I have setup a DHCP server running squid and dansguardian
squid listen on port 3128 and danguardian 8080
and i use iptables to redirect my traffic on port 8080 for my lan

i connect my windows host and dhcp works fine
but i have an internet connection 5-20 minutes later.

but if i give the the proxy address and the port to the browser, I don't have this problem

Can someone give me an advice?

---

### Post by christodoulos77 on 2007-01-04
and the same problem happens if i redirect my traffic on squid 3128

---

### Post by christodoulos77 on 2007-01-05
Nobody answer to me??

what i thick is that there is a problem with my iptables
here it is:

# squid server IP
SQUID_SERVER="192.168.1.1"
# Interface connected to Internet
INTERNET="eth0"
# Interface connected to LAN
LAN_IN="eth1"
# Squid port
SQUID_PORT="8080"

# Clean old firewall
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
# Load IPTABLES modules for NAT and IP conntrack support
modprobe ip_conntrack
modprobe ip_conntrack_ftp
# For win xp ftp client
#modprobe ip_nat_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward
# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
# Unlimited access to loop back
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
# Allow UDP, DNS and Passive FTP
iptables -A INPUT -i $INTERNET -m state --state ESTABLISHED,RELATED -j ACCEPT
# set this system as a router for Rest of LAN
iptables --table nat --append POSTROUTING --out-interface $INTERNET -j MASQUERADE
iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT
# unlimited access to LAN
iptables -A INPUT -i $LAN_IN -j ACCEPT
iptables -A OUTPUT -o $LAN_IN -j ACCEPT
# DNAT port 80 request comming from LAN systems to squid 8080
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
# DNAT port 443 request comming from LAN systems to 8080
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 443 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
# DNAT port 21 request comming from LAN systems to 8080
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 21 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
# DNAT port 70 request comming from LAN systems to 8080
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 70 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
# DNAT port 1080 request comming from LAN systems to 8080
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 1080 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
# DROP everything and Log it
iptables -A INPUT -j LOG
iptables -A INPUT -j DROP


can someone tell me if there is a problem with this file?

---

### Post by christodoulos77 on 2007-01-06
I talk to my self here???

I notice that the problem occur when i connect a second computer on server

please someone ! ! ! ! !

---

### Post by koenn on 2007-01-06
sounds familiar ... is it the same problem as this one ? [http://www.ubuntuforums.org/showthread.php?t=327994](http://www.ubuntuforums.org/showthread.php?t=327994)

on first sight, you're redirecting http (and some other) traffic to dans guardian, not to squid. I don't know dansguardian - is it supposed to work that way ?

---

### Post by christodoulos77 on 2007-01-06
thanks for the reply ! ! !

its working, but if i connect a second computer on my dhcp server its stack and needs a lot of time to work again,
unless i manually enter the proxy server ip and the port (192.168.1.1:8080) 
this is my problem.

---

