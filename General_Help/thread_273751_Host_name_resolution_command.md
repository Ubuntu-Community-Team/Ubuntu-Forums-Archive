---
title: "Host name resolution command"
date: 2006-10-08
forum: General Help
---

### Post by srunni on 2006-10-08
Hi,

Is there a terminal command that will resolve a hostname for me, printing the IP address?

Thanks

---

### Post by Sarisar on 2006-10-08
ping would work, e.g.:

> $ ping news.bbc.co.uk
PING newswww.bbc.net.uk (212.58.226.8 ) 56(84) bytes of data.
64 bytes from newslb14.thdo.bbc.co.uk (212.58.226.8 ): icmp_seq=1 ttl=55 time=11.2 ms
64 bytes from newslb14.thdo.bbc.co.uk (212.58.226.8 ): icmp_seq=2 ttl=55 time=12.8 ms
64 bytes from newslb14.thdo.bbc.co.uk (212.58.226.8 ): icmp_seq=3 ttl=55 time=12.4 ms

--- newswww.bbc.net.uk ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 11.261/12.157/12.802/0.659 ms


Of course it pings forever so ctrl+c it (ok you could run ping -c 1 xxx to run a single ping)

---

### Post by srunni on 2006-10-08
I know about ping, but I'm using this for a script where I need to get a dynamic IP address, but there's a hostname, meaning I could grep the host name resolution to get the IP address.

---

