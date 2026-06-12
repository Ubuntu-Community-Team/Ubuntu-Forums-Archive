---
title: "help with iptables..."
date: 2008-01-02
forum: General Help
---

### Post by Mia_tech on 2008-01-02
I'm having trouble appending this rule to my iptables ....anybody knows why?

jorge@ubuntu-box:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ROUTING (0 references)
target     prot opt source               destination         
jorge@ubuntu-box:~$ sudo iptables -A ROUTING -s 10.200.50.0/255.255.255.0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.200.50.3
iptables: Invalid argument

thanks

---

