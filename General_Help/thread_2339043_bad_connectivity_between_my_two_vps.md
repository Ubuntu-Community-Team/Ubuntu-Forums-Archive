---
title: "bad connectivity between my two vps"
date: 2016-10-04
forum: General Help
---

### Post by marchello_lippi2 on 2016-10-04
Hi all, I got two vps servers, let's name them A and B. I got also home computers, let's name them C1, C2, C3. I can not ping or connect from A to B and from B to A. But I can ping and connect from C1, C2, C3 to A, as well as I can ping and connect from C1, C2, C3 to B. I tried to contact system administrators of A and B servers, no luck, they both say I should contact the other side. I tried to find what are ISP between A and B using mtr, found one of them and tried to contact, but obviously they say I'm not their client, so I should contact A and B sides. What else would you suggest? I'm also in process of thinking about changing ISP for B side, but maybe someone can tell me something better. Thanks ahead.

---

### Post by TheFu on 2016-10-04
Use dig, ping and traceroute to find where the connections are being lost.  Use the public IPs for the connection attempts.  If that doesn't work, use nmap to figure out where the blocks are happening.

It is unclear how strong your network knowledge is from the posts. Are these systems on private or public networks?

---

