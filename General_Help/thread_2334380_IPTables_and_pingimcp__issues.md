---
title: "IPTables and ping/imcp  issues"
date: 2016-08-19
forum: General Help
---

### Post by Pandee on 2016-08-19
Hello!

So I have followed some guides in regards to allowing ICMP requests, Here is what I have so far in my IPTable

```

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 0 -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A OUTPUT -p icmp -m icmp --icmp-type 0 -j ACCEPT
-A OUTPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT

```

Yet I can not still ping. I have a network firewall, but I'm aware that ICMP doesn't operate at the TCP/IP level and doesn't require a port (it works on the layer 3 protocol) so it shouldn't be a problem (right?)?

---

### Post by &amp;KyT$0P# on 2016-08-19
Your iptables you posted has everything set to ACCEPT, which is same result as default.  If that is really your full iptables, your issue cannot be related to iptables.

What are you trying to ping?

---

### Post by Pandee on 2016-08-19
Hello!

Thanks for the help so far~

Well I am trying to ping an Ubuntu server from my home. The Ubuntu server is the one where im trying to set its IPTables.

---

### Post by &amp;KyT$0P# on 2016-08-19
Can you ping this Ubuntu server from a different machine that's inside the same network as the server is on?
(The idea being to get on the other side of your network firewall to see if it has a role here.)

---

### Post by Pandee on 2016-08-19
It is hosted in a different country from where I am.. So doing that is probably impossible.

---

### Post by &amp;KyT$0P# on 2016-08-19
(Well theoretically you could ssh into such a machine and do it from there, but in practice I don't know if you have any access to such a machine.)

:-k Does the network firewall log anything related to block/allow along with IP addresses, and if so do you have access to the logs?

---

### Post by Pandee on 2016-08-19
Hello!

Unfortunately I don't have another machine in the network to attempt a an internal ping.

I do have access to the network firewall.. however I don't get access to the logs :C

Anything else I can try?

---

