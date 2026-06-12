---
title: "Adding A and SRV DNS records to server."
date: 2017-07-25
forum: General Help
---

### Post by oen432 on 2017-07-25
Hi,
Using Ubuntu 14.04.5.
I'm pointing my domain to my server using my server IP address. Everything is fine but I have to add A and SRV records so ts3.cs-lucifer.pl will be pointing to specific IP and PORT.
```
A record:
ts3.cs-lucifer.pl 178.217.190.134
```
```
SRV record:
name: _tsdns._tcp
type: SRV
ttl: 3600
priority: 5
value: 10 41144 net-speak.pl
```

Tried using BIND9, edited **/etc/bind/db.local** and added these two lines at the bottom:
```
ts3.cs-lucifer.pl       IN      A       178.217.190.134
_tsdns._tcp.cs-lucifer.pl.      IN      SRV     5       10      41144   net-speak.pl
```
Then restarted bind9, but nothing is happening. I can't connect through ts3.cs-lucifer.pl. What's wrong here? What should I do?

---

