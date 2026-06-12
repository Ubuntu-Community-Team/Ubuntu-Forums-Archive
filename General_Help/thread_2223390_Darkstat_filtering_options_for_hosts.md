---
title: "Darkstat filtering options for hosts"
date: 2014-05-10
forum: General Help
---

### Post by jared20 on 2014-05-10
Hey guys!

I finally got darkstat up and running but I would like a few things filtered. I have tried a couple usage examples on the net without success. The gateway that I am running on it has a single NIC with two IP addresses. 10.0.0.254 is on eth0 and 192.168.10.254 is on eth0:0.

Here is an image of my current hosts tab:

[IMG]http://i61.tinypic.com/2z5m621.jpg[/IMG]

First of all, I would like darkstat to ignore the 10.0.0.254. I tried this without success:

-f "not (src net 10.0.0.0/24 and dst net 192.168.10.0/24)"

Secondly, I would only like to show a list of IP's that are in my local subnets (even just 192.168.10.0 /24 is fine, thats where 99% of my clients are)

Any suggestions welcome :)

Thanks!

Jared

---

