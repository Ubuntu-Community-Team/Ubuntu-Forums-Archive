---
title: "dns iptables problem"
date: 2008-06-24
forum: General Help
---

### Post by z662 on 2008-06-24
Hello, I saw a few threads on here and tried following their rules, however there must be a conflict with my script as I cannot get DNS to work with my current rule set.  Any help is greatly appreciated

heres my script (note that my webserver sits on port 8080 and my ssh is on 26662)

#!/bin/sh
# Flushing all rules
iptables -F
iptables -X
# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
# Allow unlimited traffic on loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
# Allow incoming ssh and webserver only
iptables -A INPUT -p tcp --dport 26662 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp  --sport 26662  -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp  --dport 8080  -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp  --sport 8080  -m state --state ESTABLISHED -j ACCEPT

#rule in question
# iptables -A OUTPUT -p udp --dport 53 -m state --state NEw,ESTABLISHED -j ACCEPT

ALSO having that rule enabled seems to partly work, e.g if i say, ping google.com after enabling that rule then it will just sit and wait, wheras if i comment it out like it is, after trying to ping it will say "ping unknown host google.com" - Does that mean i need a forwarding rule??

---

### Post by MythosLegend on 2008-06-24
Notice how you have sport and dport for ports 26662 and 8080.
You only have dport for port 53.
Try adding
```

iptables -A INPUT -p udp --sport 53 -m state --state NEw,ESTABLISHED -j ACCEPT

```

---

### Post by z662 on 2008-06-24
Thanks, made sense at the time too but i read on another post that the INPUT for dns was only needed if you had a DNS server running. Now that this works, this leads me to another problem...When i do sudo apt-get update, it will resolve the IP addresses, but it will not download anything, or show all the hits etc. Also when I try to ping something, it will display this: 

PING google.com (72.14.207.99) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

I understand kinda of why its blocking ping and apt-get, however I thought that once i requested either, it would be considered an existing connection, hence allowing it. Obviously I am wrong. What can I do to fix this?

---

### Post by MythosLegend on 2008-06-25
When you ping someone, it is an existing connection. The problem is that you don't have a rule to allow the protocol icmp in or out. 

This should address your pinging problem. 
```

iptables -A INPUT  -p icmp --icmp-type echo-reply -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

```
This should allow you to ping other computers, but other computers can't ping you.

I'm not sure about your sudo apt-get problem. I'm not very familiar with it but I'm going to guess that it uses a different protocol. Maybe https?

---

### Post by z662 on 2008-06-25
Thanks alot, worked great. Ill have to find out what protocol apt-get uses and then just alter one of my rules to allow it. You have been very helpful!

EDIT: got it working in less than 2 minutes... apt-get update uses http (port 80) so i just used these two rules

iptables -A OUTPUT -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

Just thought id let you know, always good to learn something too :)

---

