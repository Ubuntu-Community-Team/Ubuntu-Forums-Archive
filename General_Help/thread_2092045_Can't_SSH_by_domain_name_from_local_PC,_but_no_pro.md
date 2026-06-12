---
title: "Can't SSH by domain name from local PC, but no problem from external PC"
date: 2012-12-06
forum: General Help
---

### Post by zainka on 2012-12-06
This is my set up.

I owmn a domain, say domain.no , which is hosted by an ISP which also host a website of mine. Here I have setup an subdomain , local.domain.no , which points at my local IP. Behind my router I have a few PCs running Ubuntu and a NAS with built in ftp server. 

In my router I have setup a set of virtual servers behind diferent ports. A ftp pointing to my NAS, a ftp pointing to one of my PC and a SSH pointing to the same PC.

When I am at work I have no problem to use SSH to enter my PC using the local.domain.no url . No problem, working perfectly everytime. But try doing the same from a local PC. Nope, won't work. I can do it using the IP adr. but point was to avoid remembering IP addresses.

If i use yafc (ftp client) i can use the local.domain.no:1234 url to login to the ftp servers. But its not possible to enter via SSH from shell. I can however use SSH to access external servers, but not my local.

What do I do wrong?

---

### Post by hwttdz on 2012-12-06
I had the identical problem, with a D-Link DIR-645, a router firmware upgrade fixed it.  I don't believe I touched the config at all.

What's your router make/model?

---

### Post by zainka on 2012-12-07
Its an belkin 600db 
It already have latest firmware. so....

I cant see any settings that should prevent ssh to work when using my domain.

---

### Post by dannyboy79 on 2012-12-07
on your network what do you use for internal DNS? Also, are you saying that you have registed local.domain.no to be your external ISP provided IP address? I use hosts file within my internal network to provide hostnames to all my statically assigned IP address.

---

