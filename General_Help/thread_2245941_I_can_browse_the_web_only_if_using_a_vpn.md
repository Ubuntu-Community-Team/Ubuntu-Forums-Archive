---
title: "I can browse the web only if using a vpn"
date: 2014-09-27
forum: General Help
---

### Post by t0p on 2014-09-27
I use a phone as a wifi hotspot in order to use the web.  Recently, I have experienced a problem: the browser tells me it is "resolving host" but never connects me.

If I open a terminal and try command

```

t0p@mars:~$ ping -c 5 google.com
PING google.com (173.194.65.113) 56(84) bytes of data.
64 bytes from ee-in-f113.1e100.net (173.194.65.113): icmp_req=1 ttl=49 time=99.2 ms
64 bytes from ee-in-f113.1e100.net (173.194.65.113): icmp_req=2 ttl=49 time=298 ms
64 bytes from ee-in-f113.1e100.net (173.194.65.113): icmp_req=3 ttl=49 time=318 ms
64 bytes from ee-in-f113.1e100.net (173.194.65.113): icmp_req=4 ttl=49 time=146 ms
64 bytes from ee-in-f113.1e100.net (173.194.65.113): icmp_req=5 ttl=49 time=186 ms


--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 99.216/209.803/318.226/85.445 ms

```

So there is host resolution going on - how else would the computer know that google.com is 173.194.65.113?  Also, if I use a vpn service (eg ibVPN) I can browse the web.  But all by itself the browser can't resolve google.com - except when I'm using ping.

Anyone know what's going on?  Can I fix it?  If so, how?

Many premature thanks.

---

### Post by t0p on 2014-09-27
Oh, and before anyone suggests this: /etc/resolv.conf says 
```

nameserver 8.8.8.8
nameserver 8.8.4.4#
```

so it ain't that...

---

### Post by Lars Noodén on 2014-09-27
That lets ICMP through.  What about TCP on port 80?

```

sudo traceroute -T www.google.com

```

---

