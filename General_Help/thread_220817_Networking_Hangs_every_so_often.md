---
title: "Networking Hangs every so often"
date: 2006-07-22
forum: General Help
---

### Post by rupy on 2006-07-22
Hi guys,

The networking seems to go screwey on my ubuntu install about twice a day, its REALLY annoying.

Basically I cant browse to any new sites, but address's that I have already been to work fine and my messenging program stays connected, I have to restart my eth0 interface - sudo ifdown eth0; sudo ifup eth0.

Its not DNS related cos I can resolve new uncached address's.

---

### Post by rupy on 2006-07-23
Any idea's?

---

### Post by ubuntu-geek on 2006-07-23
Hmm it could be possible your DHCP isnt renewing correctly from your router, that is if you are using a DHCP server. 

Some more questions..

When you cannot browse can you still ping from a terminal window? For example?

```
ping www.yahoo.com
``` 

How is your network setup?

---

### Post by rupy on 2006-07-24
I am using a manual set IP address, although there is a DHCP server here.

My network settings are as follows:
> 
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 172.16.236.151
netmask 255.255.0.0
gateway 172.16.236.254


Pretty standard....

I'll do some testing when the network hang occurs.

---

