---
title: "reverse DNS?"
date: 2008-02-13
forum: General Help
---

### Post by Sir P on 2008-02-13
hello all,

I'm aware how to use the nslookup and dig commands to return hostnames/ips etc however I have been asked to setup reverse DNS on my ubuntu server.

What does he mean by setup reverse DNS and how do I go about it?

Any information would be much apperciated

Warm Regards
Sir P :D

---

### Post by mbeierl on 2008-02-13
[http://en.wikipedia.org/wiki/Reverse_DNS_lookup](http://en.wikipedia.org/wiki/Reverse_DNS_lookup)

I don't know who would ask you to set up "reverse dns"; perhaps they meant a DNS server?  Why where you asked to do this?  The reason for the question is that playing with DNS can cause problems for other users.

---

### Post by Sir P on 2008-02-13
hi there

Thanks for your reply.

The reason they asked for this is because there is no reverse dns currently on the server and it causes connection problems when trying to connect to remote servers.. for authentication and packet loss reasons

many thanks :)

---

### Post by mbeierl on 2008-02-13
I think I get the picture.  So, I've had a similar situation like so:
```

       firewall
          !   +---+
          !   |DNS|
+------+  !   +---+
|server|  <  +------+
+------+  !  |client|
          !  +------+

```
Client tries to get to server, and can do so because firewall allows it.  Server receives connection, attempts to do reverse DNS lookup on it, but can't because firewall prevents it from accessing DNS server.  Connection takes a long time before DNS query timeout occurs, then finally succeeds and connection is audit logged by IP address only.

This can be drawn any number of ways, but the bottom line comes down to the server being unable to look up a name for the client's IP address - hence the request for "reverse dns lookup."

What is needed in this case is not a mythical reverse dns server, but simply a resolver.  A resolver can be as simple as putting entries into /etc/hosts, or as full fledged as running your own dns server.

If it is a limited number of clients that are connecting, and their ip addresses are known, the /etc/hosts route is definitely the way to go.  I'm afraid I cannot give you much advice on setting up a DNS server.  The only experience I've had was totally small time (15-20 workstations) using dnsmasq to act as both the DNS server and DHCP server.

---

