---
title: "Internet connectivitiy problems"
date: 2006-08-11
forum: General Help
---

### Post by trinityj5 on 2006-08-11
Hi there,

I'm totally new to linux, so please keep your explanations simple!

Upon installing Ubuntu, I got dhcp leases from my router, and could resolve hostnames and ping addresses (eg. ping [www.google.com](www.google.com) worked ok) but could not access the internet

Googling revealed this post: [http://www.ubuntuforums.org/archive/index.php/t-5690.html]("http://www.ubuntuforums.org/archive/index.php/t-5690e.html")
which describes my problem. 

So I disabled IPv6 in firefox's about:config, which made firefox work, but obviously apt, etc, still don't work.

So I disabled IPv6 system-wide, according to the post here: [http://www.ubuntuforums.org/showthread.php?t=87798]("http://www.ubuntuforums.org/showthread.php?t=87798")
and rebooted.

No sit0 interface is present in ifconfig -a, so IPv6 is at least partly disabled, yet still synaptic doesn't work.

Any ideas?

John

---

