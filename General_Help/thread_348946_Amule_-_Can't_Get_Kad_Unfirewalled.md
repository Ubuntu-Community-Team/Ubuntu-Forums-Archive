---
title: "Amule - Can't Get Kad Unfirewalled"
date: 2007-01-29
forum: General Help
---

### Post by Ingla on 2007-01-29
Hello. 

I'm running aMule 2.1.3 on Dapper. I get "kad firewalled" and, after a while, "kad off".

I using a router (TNN-SIEMENS C2-010).

-----------------------------------------------------------------------------------------------------------------------------------
ROUTER SETTINGS
-----------------------------------------------------------------------------------------------------------------------------------
Port forwarding is set in the router to open the following ports:

4662
4672
4665
65535 (saw on some forum that that should also be open)

Filters show:
Outbound Filter List
1	Any IP	Any IP	0~65535	0~65535	UDP	Allow
-----------------------------------------------------------------------------------------------------------------------------------
OUTPUT of iptables -L
-----------------------------------------------------------------------------------------------------------------------------------
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
-----------------------------------------------------------------------------------------------------------------------------------

I think that output should be showing something about UDP, etc., but as you can see it doesn't.

If I try to update nodes, I get an error that the file was not downloaded. If I disconnect kad and hit "Bootstrap from Known Clients" (whatever that means) I see brief activity on the graph but kad is still firewalled and soon turns off.

Can anyone see what's wrong and how I can get kad working?

Any help appreciated. I've tried everything I can think of.

Thanks.

---

### Post by TheWizzard on 2007-01-29
i'm also forwarding port 4711 (TCP)

try disabling your firewall (temporary).

if i'm not mistaken, you need to be downloading a file with amule. i don't know why, but i tested this and it makes a difference.

---

### Post by Ingla on 2007-01-29
Thanks.

I'll try the port. I'm not running a firewall unless Dapper has one I don't know about. I turned off the one in the router.

---

### Post by TheWizzard on 2007-01-30
> **Ingla said:**
> Thanks.

I'll try the port. I'm not running a firewall unless Dapper has one I don't know about. I turned off the one in the router.

the default firewall is iptables. i don't know much about the default settings. 
you can try installing and running firestarter. this is a gui front end for iptables and allows you to stop all filtering.
hope this helps.

---

### Post by zatoichiino on 2007-12-13
I resolved that problem, lets try to add UDP ports to your iptables. In the amule manulas is writed to add TCP+3 like 4662+3=4665, do that with UDP like 4672+3=4675. For me kad is working now with no problem:)

---

### Post by zatoichiino on 2007-12-14
In my previous configuration, I saw a problem, not with kad id, but with a transfer. This is my new configuration of iptables.   

iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
iptables -A INPUT -p tcp --dport 4661 -j ACCEPT
iptables -A INPUT -p udp --dport 4662:4665 -j ACCEPT
iptables -A INPUT -p udp --dport 4672 -j ACCEPT
iptables -A INPUT -p udp --dport 4675 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 4662:4665 -j ACCEPT
iptables -A OUTPUT -p udp --dport 4672 -j ACCEPT
iptables -A OUTPUT -p udp --dport 4675 -j ACCEPT


Now the transfer is just grate :lolflag:

---

### Post by zatoichiino on 2007-12-14
Small correction 

iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
iptables -A INPUT -p tcp --dport 4661 -j ACCEPT
iptables -A INPUT -p udp --dport 4662:4665 -j ACCEPT
iptables -A INPUT -p udp --dport 4672 -j ACCEPT
iptables -A INPUT -p udp --dport 4675 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 4662 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 4661 -j ACCEPT
iptables -A OUTPUT -p udp --dport 4662:4665 -j ACCEPT
iptables -A OUTPUT -p udp --dport 4672 -j ACCEPT
iptables -A OUTPUT -p udp --dport 4675 -j ACCEPT

Now is amazing, I thing this is a final :)

---

### Post by relja on 2008-06-07
Bravo!
Thanks zatoichiino a lot.
Had same problem but you have solved it for me :)

---

