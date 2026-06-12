---
title: "Firefox and youtube"
date: 2008-06-25
forum: General Help
---

### Post by TimoS on 2008-06-25
I wonder if anybody can help me. For some reason whenever I go to [http://www.youtube.com](http://www.youtube.com) Firefox automatically redirects me to [http://jp.youtube.com](http://jp.youtube.com) Of course the same videos and everything is there, but since the user interface is in japanese, it makes it harder to use. Any ideas on how to fix this?

---

### Post by p_quarles on 2008-06-25
You could always use the numeric IP address:
```
208.65.153.251
```
Of course, that's kind of a ridiculous workaround, but if that works, you would at least know that this is a DNS issue. If not, it probably has to do with language settings in Firefox.

---

### Post by TimoS on 2008-06-25
Yes, that seems to work, but like you said, it is a bit silly workaround

---

### Post by p_quarles on 2008-06-25
Well, like I also said, it narrows down the source of the problem to a domain name server between you and YouTube. Try this:
```
traceroute www.youtube.com
```
and post the results here.

---

### Post by TimoS on 2008-06-25
1  home.gateway (192.168.0.254)  3.290 ms  3.334 ms  3.443 ms
 2  10.0.33.1 (10.0.33.1)  20.346 ms  20.420 ms  22.912 ms
 3  213.157.93.254 (213.157.93.254)  59.688 ms  61.808 ms  62.239 ms
 4  r1-ge1.hki.nbl.fi (217.30.183.140)  63.989 ms  66.501 ms  66.945 ms
 5  83.145.236.146 (83.145.236.146)  69.349 ms  71.573 ms  74.190 ms
 6  64.209.110.193 (64.209.110.193)  75.955 ms  122.537 ms  38.422 ms
 7  208.49.224.118 (208.49.224.118 )  138.270 ms  138.598 ms  139.083 ms
 8  * * *
 9  * * *
10  * * *
11  youtube.com (208.65.153.238 )  232.019 ms * *


Don't know if this matters, but on my old laptop I'm running Fedora 9, and there this problem doesn't occur eventhough they're both in the same network

---

### Post by p_quarles on 2008-06-25
Well, that doesn't show anything (that I can see).

I remember someone else having a similar name resolution problem, and it turned out the Gnome network manager had done some strange things to /etc/hosts. What's in that file?

---

### Post by TimoS on 2008-06-25
timo@usagi:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 usagi

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by RagingAardvark on 2008-06-25
Where do you get redirected to when you visit Google?

---

### Post by TimoS on 2008-06-25
> **RagingAardvark said:**
> Where do you get redirected to when you visit Google?

I'll double-check when I get home, but I'm fairly sure it goes to google.fi

edit: just checked and I was correct, [http://www.google.com](http://www.google.com) redirects to [http://www.google.fi](http://www.google.fi)

---

