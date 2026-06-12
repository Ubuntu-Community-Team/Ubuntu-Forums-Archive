---
title: "How do I have an outsider connect to my ip"
date: 2007-08-19
forum: General Help
---

### Post by xavier_r on 2007-08-19
Ok first let me tell what I have done...

1. Apache runs perfectly, [http://localhost/](http://localhost/)  or [http://127.0.0.1/](http://127.0.0.1/) or 10.28.43.217 which is my eth0 inet addr displays my web site correctly...

2. I have dynamic IP, so I have setup no-ip, and I have also setup a domain name in no-ip... mydomain.com(say)

Now theoretically, if I connect to mydomain.com I should be able to see my web-site...
But nothing happens...

---

### Post by jnorthr on 2007-08-19
from a terminal command line can you 'ping xxx' any of your ip addresses successfully ?

---

### Post by OoooMatron on 2007-08-19
have you opened port 80 on your router and firewall (if you ahve one).

---

### Post by xavier_r on 2007-08-19
> **jnorthr said:**
> from a terminal command line can you 'ping xxx' any of your ip addresses successfully ?

No

> have you opened port 80 on your router and firewall (if you ahve one).

I have a direct cable connection... no router or firewall... (and apache is configured for port 80)

---

### Post by kevinatkins on 2007-08-19
It's possible your ISP might be blocking port 80 - perhaps you could try running Apache on a different port and see what happens?

---

### Post by xavier_r on 2007-08-19
> **kevinatkins said:**
> It's possible your ISP might be blocking port 80 - perhaps you could try running Apache on a different port and see what happens?

I tried 8080, 8183 and some other ports, but no its not working...
Could you tell some sample ports which you think hopefully most ISPs dont block ?

EDIT: I am trying the "port 80 redirect" service in no-ip lets see what happens
EDIT: Nothing Happened, same situation

---

### Post by kevinatkins on 2007-08-19
Hi,

AFAIK, you should be able to use any port from 1023 upwards, which are unprivileged ports. Check you haven't got any other services accepting connections at the port you choose.

However, there is one other possibility, which is that it may be a DNS problem if you're attempting to connect to the external address of your machine from within the local network - this caught me out. You could try connecting to your website from a friend's machine, see if that works.

---

### Post by xavier_r on 2007-08-19
> **kevinatkins said:**
> 
However, there is one other possibility, which is that it may be a DNS problem if you're attempting to connect to the external address of your machine from within the local network - this caught me out. You could try connecting to your website from a friend's machine, see if that works.

Can I use a thin client?
I mean like NXClient?
I have a remote desktop account at cosmopod.com

EDIT: Nope this doesnt work either
I just cant imagine what the problem can be :(

---

### Post by xavier_r on 2007-08-20
Anyone please?

---

### Post by thrcomputer on 2007-08-20
Check the following:

Router
If you have a router, make sure you have port 80 opened up.  On linksys routers that have a port at the end that has no restrictions on it.

Linux
Check your linux firewall and make sure you have port 80 opened up.

You DNS Service
Depending on the service, it can take up to 24 hours + for the domain to be visible on the internet.

Have you tried to simply type in your current ip address and see it it hits your webserver??  This is an easy way to see if your ISP is doing some sort of port blockings.

If you determine that your isp is doing blocking, you will need to modify your webserver running port and then go back to your dns service and make sure they are forwarding to the correct port.  I know that when I used zone edit, you have to specific the port that the traffic was going to get forwarded to.

Hope that helps.

---

### Post by xavier_r on 2007-08-21
> **thrcomputer said:**
> 
If you determine that your isp is doing blocking, you will need to modify your webserver running port and then go back to your dns service and make sure they are forwarding to the correct port.  I know that when I used zone edit, you have to specific the port that the traffic was going to get forwarded to.

I have scanned using nmap, and it seems my ISP is blocking ports...
Its stupid...
I am just trying to find out one port, just one open port...
And have found none... :(
Any suggestions after these vain attempts?

---

### Post by xavier_r on 2007-08-21
Does UBUNTU have any in-built default firewall that blocks incoming requests ?

---

