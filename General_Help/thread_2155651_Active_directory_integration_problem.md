---
title: "Active directory integration problem"
date: 2013-06-19
forum: General Help
---

### Post by uzumakifahim on 2013-06-19
I'm trying to connect an Ubuntu 12.04 workstation with an active directory setup. I've installed **likewise-open** and **likewise-open-gui, **but I'm getting the following error (Please check the attached image). 

Please help anyone. Thanks in advance.

---

### Post by zero2xiii on 2013-06-19
Hay,

Can you please be a little more specific as to the location of the pc you are trying to connect to, is it in your LAN or outside (over VPN or internet maybe).
Are you using the domain-name of the computer or an IP address? Are you allowed by that computer's firewall to connect. Does you software versions match?

Can you "see" the other computer if you ping it:
```
ping **IP_ADDRESS_OF_OTHER_PC**
PING www.google.com (74.125.233.83) 56(84) bytes of data.
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=1 ttl=54 time=343 ms
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=2 ttl=54 time=329 ms
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=3 ttl=54 time=366 ms
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=4 ttl=54 time=388 ms
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=5 ttl=54 time=250 ms

```

This will help us greatly in helping you further.

---

### Post by Crashoverload on 2013-06-19
Check whether the system Time of Server and Client is the same. That could be a problem.
Another issue could be, that you dont have entered the correct connection data for your domain.

---

### Post by uzumakifahim on 2013-06-19
> **zero2xiii said:**
> Hay,

Can you please be a little more specific as to the location of the pc you are trying to connect to, is it in your LAN or outside (over VPN or internet maybe).
Are you using the domain-name of the computer or an IP address? Are you allowed by that computer's firewall to connect. Does you software versions match?

Can you "see" the other computer if you ping it:
```
ping **IP_ADDRESS_OF_OTHER_PC**
PING www.google.com (74.125.233.83) 56(84) bytes of data.
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=1 ttl=54 time=343 ms
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=2 ttl=54 time=329 ms
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=3 ttl=54 time=366 ms
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=4 ttl=54 time=388 ms
64 bytes from jnb01s02-in-f19.1e100.net (74.125.233.83): icmp_req=5 ttl=54 time=250 ms

```

This will help us greatly in helping you further.

Thanks for your reply. I'm answering your question one by one - 

1. I'm trying to connect in my LAN.
2. I'm trying using domain-name.
3. I don't check about the firewall. Could you tell me please, how can I check that?
4. About software version, please tell me which software do I need to match?

---

### Post by zero2xiii on 2013-06-19
Hay,

> 2. I'm trying using domain-name.

The quickest way to rule out other possible problems is by trying first to connect via IP address, if any of the other problems are to blame this will fail as well and then we can start working them out one by one. If the connect with IP works, try running a ping on the host name and see what errors you get:

```
ping some-hostname
```

you can also do a tracepath to the host name to see where the error occurs (try the IP if this fails):

```
tracepath some-hostname
```

This should give us an idea. Also using the IP in the above command will give a host name, use this hostname instead of one you are using for example if a tracepath to my router:
```
~/:~$ tracepath 192.168.1.1
 1:  Somedomain.local                                     0.122ms pmtu 1500
 1:  router.com.where.gateway                               1.739ms reached
 1:  router.com.where.gateway                               1.210ms reached
     Resume: pmtu 1500 hops 1 back 64 

```

So my router's domain can also be: router.com.where.gateway

Hope that makes sense.

---

### Post by uzumakifahim on 2013-06-20
> **zero2xiii said:**
> Hay,



The quickest way to rule out other possible problems is by trying first to connect via IP address, if any of the other problems are to blame this will fail as well and then we can start working them out one by one. If the connect with IP works, try running a ping on the host name and see what errors you get:

```
ping some-hostname
```

you can also do a tracepath to the host name to see where the error occurs (try the IP if this fails):

```
tracepath some-hostname
```

This should give us an idea. Also using the IP in the above command will give a host name, use this hostname instead of one you are using for example if a tracepath to my router:
```
~/:~$ tracepath 192.168.1.1
 1:  Somedomain.local                                     0.122ms pmtu 1500
 1:  router.com.where.gateway                               1.739ms reached
 1:  router.com.where.gateway                               1.210ms reached
     Resume: pmtu 1500 hops 1 back 64 

```

So my router's domain can also be: router.com.where.gateway

Hope that makes sense.

WOW!!! Great reply. I'll post the O/P here in time. Thanks.

---

