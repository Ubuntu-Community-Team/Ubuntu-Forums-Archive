---
title: "HOWTO: SAMBA with Bastille"
date: 2008-03-01
forum: General Help
---

### Post by Oldsoldier2003 on 2008-03-01
After an aborted attempt to manually write my Iptables rules , I set up Bastille to harden my LAMP/SAMBA Server.

Bastille is pretty easy to use but upon further testing iI found that although Bastille did an admirable job of setting up iptables, adding the Samba required ports by running Bastille in the interactive mode did not work. All my rules worked but I could not connect to my samba server form inside my own network.

Heres the fix. in your /etc/Bastille/firewall.d directory create a file named pre-chain-split.sh

```
iptables -A INPUT -s 192.168.0.0/24 -p udp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
iptables -A INPUT -s 192.168.0.0/24 -p tcp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
iptables -A OUTPUT -s 192.168.0.0/24 -p udp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
iptables -A OUTPUT -s 192.168.0.0/24 -p tcp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
```

this code will execute and apply these rules before the exceptions created in the default setup Bastille makes when you run it in the interactive mode, thus enabling you to connect from your local subnet.

---

