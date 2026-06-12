---
title: "konqueror don't surf."
date: 2007-12-28
forum: General Help
---

### Post by israelha on 2007-12-28
Hi all, first i appologize if i have english grammar errors.
so i have a problem with Konqueror.
always whem i try to surf to Google.com or any another website i get this output:
```
An error occurred while loading http://www.google.com/search?q=lol&ie=UTF-8&oe=UTF-8:
Could not connect to host http://www.google.com/search?q=lol&ie=UTF-8&oe=UTF-8.
```

please help me.
Thamks a lot!

---

### Post by Craigus on 2007-12-28
What happens if you do:

> ping [www.google.com](www.google.com)

---

### Post by israelha on 2007-12-29
> **Craigus said:**
> What happens if you do:

OUTPUT:

```
PING www.google.com (64.233.183.99) 56(84) bytes of data.
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=1 ttl=241 time=119 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=2 ttl=241 time=128 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=3 ttl=241 time=118 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=4 ttl=241 time=128 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=5 ttl=241 time=118 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=6 ttl=241 time=128 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=7 ttl=241 time=147 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=8 ttl=241 time=127 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=9 ttl=241 time=128 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=10 ttl=241 time=117 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=11 ttl=241 time=128 ms
64 bytes from nf-in-f99.google.com (64.233.183.99): icmp_seq=12 ttl=241 time=126 ms

```

---

### Post by Craigus on 2007-12-29
Try shutting down KNetworkManager - can you surf with Konq then ?

I think this may be a known bug.

---

