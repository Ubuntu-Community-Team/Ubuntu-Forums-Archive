---
title: "internet weirdly slow"
date: 2004-10-25
forum: General Help
---

### Post by sfw5000 on 2004-10-25
Hi -- I just set up an Ubuntu machine for a friend. This is his first experience with linux. When he set up his machine at home everything went fine, except he says web pages are taking _forever_ to load. He went to a site that tests connection speeds and everything was normal. But in browsing the web, everything is really slow. This seems weird to me. When I set up his computer this was not happening at all -- everything was fine. The only difference is that I set it up on a network with a router, and now he is conencted directly to the net via his DSL modem -- no router.

Would that make a difference? Anyone hear of something like this?

---

### Post by jdong on 2004-10-25
This is an annoying problem that happens when IPv6 is enabled. Mozilla browsers seem to like to query IPv6 DNS for websites. See [http://www.ubuntuforums.org/showthread.php?t=171](http://www.ubuntuforums.org/showthread.php?t=171)

---

### Post by sfw5000 on 2004-10-25
Thanks -- totally makes sense. I'll try that out.

Sam

---

### Post by jdong on 2004-10-25
lol, post-thread defense mode enabled:

This is _NOT_ a ubuntu problem. More of a ipv6 problem. It first happened with Fedora Core 1, then other distros started getting this problem, too, as their autodetectors inserted ipv6.ko...

Even Windows with IPV6 enabled has intermittent DNS headaches.

---

