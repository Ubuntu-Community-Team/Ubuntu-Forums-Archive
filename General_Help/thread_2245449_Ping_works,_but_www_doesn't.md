---
title: "Ping works, but www doesn't?"
date: 2014-09-23
forum: General Help
---

### Post by t0p on 2014-09-23
I connect to the internet by tethering an Android phone.  This evening, I can't connect to the web.  The internet connection itself is working, as evidenced by my pinging:

```

t0p@mars:~$ ping -c 5 gogle.com
^C
t0p@mars:~$ ping -c 5 gogle.com
PING gogle.com (74.125.230.116) 56(84) bytes of data.
64 bytes from lhr14s24-in-f20.1e100.net (74.125.230.116): icmp_req=1 ttl=48 time=149 ms
64 bytes from lhr14s24-in-f20.1e100.net (74.125.230.116): icmp_req=2 ttl=48 time=189 ms
64 bytes from lhr14s24-in-f20.1e100.net (74.125.230.116): icmp_req=3 ttl=48 time=190 ms
64 bytes from lhr14s24-in-f20.1e100.net (74.125.230.116): icmp_req=4 ttl=48 time=198 ms
64 bytes from lhr14s24-in-f20.1e100.net (74.125.230.116): icmp_req=5 ttl=48 time=247 ms


--- gogle.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 149.914/195.250/247.989/31.315 ms

```

But when I try to access websites via browsers (Chromium and Firefox) it tells me it's connecting but ever does connected.  Actually, that's Firefox; Chromium just sits there telling me it's resolving the site.

I haven't changed any net or browser settings since this morning, which was the last time I could access the web.  And ping's working.  Soi, anyone help me with this flabbergastedness?

Incidentally, I'm posting this via my laptop tethered to another Android pay-as-you go phone that hasn't actually got any credit on it.  Anoher flabbergaster.  Bit I'd like to fix the other problem, before my ISP realises I'm getting the net for nothing and goes all medieval on my a**, or whatever it is they do to miscreants nowadays...

---

### Post by Michael_McKenney on 2014-09-23
Did you configure your gateway address to your phone's ip.  You also need to configure DNS servers.

---

### Post by Habitual on 2014-09-23
nameserver 8.8.8.8
nameserver 8.8.4.4
in /etc/resolv.conf

---

### Post by t0p on 2014-09-27
> **Habitual said:**
> nameserver 8.8.8.8
nameserver 8.8.4.4
in /etc/resolv.conf
Did that.  No good.  Sad.

---

