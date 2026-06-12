---
title: "How to prefer IPv6"
date: 2017-07-24
forum: General Help
---

### Post by Skaperen on 2017-07-24
apparently, programs like web browsers prefer to connect to the address that arrives first.  this is rarely IPv6 because queries seem to be made for IPv4 first.

oddly, the connection choice does not seem to be made based on whether the answer arrives via IPv6 or IPv4.  i put "nameserver 2001:4860:4860::8844" and "nameserver 2001:4860:4860::8888" as the first two entries in my /etc/resolv.conf file, but this had no effect other then to increase the IPv6 traffic over my tunnel a bit.

i would like to get a behavior where most connections go by way of IPv6 if that host has a working IPv6 address.  if there is no AAAA record then clearly not.  there can be cases where an AAAA record arrives but their IPv6 is misconfigured and does not work.  hopefully the latter case is rare and probably not worth worrying about.

**has anyone done a configuration change to Ubuntu 16.04 to achieve this that they would like to share?**

one idea i had requires a means to have all IP traffic (or at least port 53 traffic) go through my own program (i don't know how to accomplish this).  my program would delay all port 53 traffic answering with only an A record a specific number of nanoseconds.  i do se A record and AAAA answers arriving separately so i should not need to split any answers (there is no such query to ask for both A and AAAA together ... separate queries are required so it is reasonable to assume separate answers).

**does anyone know how to run such traffic into such a program?**

i do not want to do this as a kernel hack or kernel module.  i want to have all i do stay in user space with at most root privs.

---

### Post by unityforever on 2017-07-24
amateur just pass by...

how about disable IPv4 function completely...? :D just kidding

---

### Post by Skaperen on 2017-07-26
> **uiduser said:**
> amateur just pass by...

how about disable IPv4 function completely...? :D just kidding

yeah, i don't think that would work ;)

what they (whoever they are) should do is modify DNS cache servers so that if a recursive query arrives to it via IPv6 for an A record, it should delay it by an admin configurable interval of time.  that way clients using IPv6 and doing nearly parallel AAAA and A queries would get the AAAA answer first.  i wonder if i could wedge this into OpenVPN (i use that to do IPv6 and have my [FONT=courier new]/etc/resolv.conf[/FONT] pointing at IPv6 addresses).

---

