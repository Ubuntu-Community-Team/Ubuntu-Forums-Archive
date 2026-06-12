---
title: "help with output from ping"
date: 2008-06-11
forum: General Help
---

### Post by monkeyking on 2008-06-11
Hi,

I'm having problems understandig the output from the ping command.
Can someone elaborate on why the hostname changes every time.
I'm killing the ping with ctrl-c

thanks in advance
```

ping opt3
PING opt3.dow.se (192.38.113.219) 56(84) bytes of data.
64 bytes from zm129ibm (192.38.113.219): icmp_seq=1 ttl=64 time=0.184 ms
64 bytes from opt3.dow.se (192.38.113.219): icmp_seq=2 ttl=64 time=0.194 ms
64 bytes from zm129ibm (192.38.113.219): icmp_seq=3 ttl=64 time=0.196 ms
64 bytes from opt3.dow.se (192.38.113.219): icmp_seq=4 ttl=64 time=0.191 ms
64 bytes from zm129ibm (192.38.113.219): icmp_seq=5 ttl=64 time=0.192 ms
64 bytes from opt3.dow.se (192.38.113.219): icmp_seq=6 ttl=64 time=0.188 ms
64 bytes from zm129ibm (192.38.113.219): icmp_seq=7 ttl=64 time=0.190 ms
64 bytes from opt3.dow.se (192.38.113.219): icmp_seq=8 ttl=64 time=0.187 ms
64 bytes from zm129ibm (192.38.113.219): icmp_seq=9 ttl=64 time=0.190 ms

--- opt3.dow.se ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8002ms
rtt min/avg/max/mdev = 0.184/0.190/0.196/0.009 ms


```

---

### Post by RealPSL on 2008-06-11
Wow that is interesting. Is it possible that the IP address resolves to 2 different names?

---

### Post by monkeyking on 2008-08-21
The switch, was apperently not working corretly

---

