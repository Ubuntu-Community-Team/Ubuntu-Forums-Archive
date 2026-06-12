---
title: "iptables Block host after attempted connection"
date: 2016-10-19
forum: General Help
---

### Post by signpost2 on 2016-10-19
Hi,

Bit of a strange question. I'm listening to a port on my machine for activity but what I want to do is write a script which takes the IP address of anyone who tries to connect and block that host from connecting 
I've an iptable rule started:

iptables -I INPUT -p tcp -m tcp --dport 1111 -m state --state NEW  -j LOG --log-level 1 --log-prefix "New Connection Attempt"

This logs the ip address source into the log file /var/log/syslog. I'm thinking next I should write a bash script to grep through this file and find the IP, is it then possible to add a new rule to my iptables to drop this ip address?

---

### Post by Habitual on 2016-10-19
fail2ban does this already.
Have a look at it.

---

