---
title: "How Do I Create a PUBLIC Proxy Server With Squid?"
date: 2008-06-25
forum: General Help
---

### Post by blazercist on 2008-06-25
Basically I need some instructions on how I can create a proxy server with squid that is accessible from WAN.

HERES A DIAGRAM:

      
[REMOTE CLIENT] --> [INTERNET] --> [ROUTER] --> [SQUID] --> [INTERNET] 


The reason for this is quite simple, I'm in a place where there are very silly admins that are using a proxy to monitor net traffic on port 80, basically they setup a proxy server that uses port 8080 and they blocked off port 80 so that all the http traffic is funneled through the proxy server to be monitored.

BUT, they didn't block any of the other ports :)  For example I can ssh into my home PC no problem.

So what I wanna do is setup squid on my home pc to accept connections on a weird port so that I may avoid the web proxy entirely.  I hope that makes sense.

In order for there not to be a bunch of substitution I will give you certain variable values that you may need.

the port I want the proxy to listen on: 3128
my local ip on the machine running the server: 192.168.0.102
my routers ip: 192.168.0.1
I have port forwarding already setup to accept requests from WAN on 3128 and send them to 192.168.0.102:3128

For now I don't want there to be any authentication regarding the proxy, I will add that after I have tested it and determined that it works.

Please help me configure squid.conf correctly.

---

### Post by bodhi.zazen on 2008-06-25
> **blazercist said:**
> Basically I need some instructions on how I can create a proxy server with squid that is accessible from WAN.

HERES A DIAGRAM:

      
[REMOTE CLIENT] --> [INTERNET] --> [ROUTER] --> [SQUID] --> [INTERNET] 


The reason for this is quite simple, I'm in a place where there are very silly admins that are using a proxy to monitor net traffic on port 80, basically they setup a proxy server that uses port 8080 and they blocked off port 80 so that all the http traffic is funneled through the proxy server to be monitored.

BUT, they didn't block any of the other ports :)  For example I can ssh into my home PC no problem.

So what I wanna do is setup squid on my home pc to accept connections on a weird port so that I may avoid the web proxy entirely.  I hope that makes sense.

In order for there not to be a bunch of substitution I will give you certain variable values that you may need.

the port I want the proxy to listen on: 3128
my local ip on the machine running the server: 192.168.0.102
my routers ip: 192.168.0.1
I have port forwarding already setup to accept requests from WAN on 3128 and send them to 192.168.0.102:3128

For now I don't want there to be any authentication regarding the proxy, I will add that after I have tested it and determined that it works.

Please help me configure squid.conf correctly.

Sounds too shady to me.

---

