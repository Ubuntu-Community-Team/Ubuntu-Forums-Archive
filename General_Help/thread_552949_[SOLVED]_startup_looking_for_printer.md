---
title: "[SOLVED] startup looking for printer"
date: 2007-09-17
forum: General Help
---

### Post by gishaust on 2007-09-17
Hello everyone

I am running ubuntu with a gui. When I start it up it takes forever and says that there is an error with one of the dameons. I looked at the error system logs and it says,

E [17/Sep/2007:19:12:28 +1000] Creating missing directory "/var/run/cups/certs"
E [17/Sep/2007:19:12:28 +1000] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.

I am assuming that it is looking for the printer  which is on another network computer and is not turned on. Is there a way to get it to speed up the process. Instead of taking 5mins.

As a side point I am starting to love ubuntu.

Gishaust

---

### Post by dcstar on 2007-09-18
> **gishaust said:**
> Hello everyone

I am running ubuntu with a gui. When I start it up it takes forever and says that there is an error with one of the dameons. I looked at the error system logs and it says,

E [17/Sep/2007:19:12:28 +1000] Creating missing directory "/var/run/cups/certs"
E [17/Sep/2007:19:12:28 +1000] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.

I am assuming that it is looking for the printer  which is on another network computer and is not turned on. Is there a way to get it to speed up the process. Instead of taking 5mins.

As a side point I am starting to love ubuntu.

Gishaust

127.0.0.1 is your own "internal" IP address, possibly there is another networking issue that this error is just a symptom of.

Post the contents of your /etc/hosts file, and also the output of the following commands:
```
hostname -v
hostname -a
```

---

### Post by gishaust on 2007-09-22
Thanks david

 i will have a look at the host

---

