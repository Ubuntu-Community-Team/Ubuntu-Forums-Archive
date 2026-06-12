---
title: "Network Traffic Analysis"
date: 2005-10-04
forum: General Help
---

### Post by gushy on 2005-10-04
Currently I use ethereal to monitor our my company network, however it's only really useful for performing small snapshots and analysis of the data is a slow manual process.
Anyone know of something that I can run that can produce reports (once I setup filters etc) telling me what PC has been doing what?  I really need to be able to go into detail - eg. Joe Bloggs was streaming sky sports broadband, fred brown was surfing ebay for minidisc players for 2 hours, jane white was downloading using gnutella at an average of 120k/sec etc.
I could probably install a web proxy and log all web traffic (at least I think I could) but I could do with being able to see all traffic, and getting back reports.

---

### Post by fabiand on 2005-10-06
Hey,

maybe not as detailed as you need it, but have a look at ntop.
you will need to install it on your gateway or setup some kind of trunking on your switch ..

- fabiand

---

### Post by katu on 2005-10-06
You could try darkstat. It seems to do most of the stuff you need.
[http://dmr.ath.cx/net/darkstat/](http://dmr.ath.cx/net/darkstat/)
It seems it's discontinued but there is a package in ubuntu. I don't know how it works, I'll check it out when I get home...

---

### Post by gushy on 2005-10-06
fabiand:  yeah I use ntop, I use that for a quick overview (and iftop as well) but it doesn't provide enough detail for analysis

katu:  not heard of that one before, I'll have to check it out.

---

