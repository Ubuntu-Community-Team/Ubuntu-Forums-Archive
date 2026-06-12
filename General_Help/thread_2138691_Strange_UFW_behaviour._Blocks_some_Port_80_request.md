---
title: "Strange UFW behaviour. Blocks some Port 80 requests when told not to."
date: 2013-04-25
forum: General Help
---

### Post by hkphooey on 2013-04-25
Hi,

I have UFW installed on a webserver. I've asked it nicely to allow web traffic, and my ssh traffic on a non-standard port:
```
webserver:~# ufw status
Status: active
To                         Action      From
--                         ------      ----
222                        ALLOW       Anywhere
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
222                        ALLOW       Anywhere (v6)
80                         ALLOW       Anywhere (v6)
443                        ALLOW       Anywhere (v6)
```

However, when I look through the UFW logs, I see that some requests on Port 80 are being blocked:
```
server:> grep "DPT=80" /var/log/ufw.log | more
Apr 21 03:28:44 blog kernel: [8550050.929758] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=99.177.92.3 DST=10.10.10.5 LEN=40 TOS=0x
00 PREC=0x00 TTL=115 ID=4850 DF PROTO=TCP SPT=50027 DPT=80 WINDOW=4271 RES=0x00 ACK FIN URGP=0 
Apr 21 03:29:03 blog kernel: [8550070.176027] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=99.177.92.3 DST=10.10.10.5 LEN=40 TOS=0x
00 PREC=0x00 TTL=115 ID=5033 DF PROTO=TCP SPT=50025 DPT=80 WINDOW=0 RES=0x00 ACK RST URGP=0 
Apr 21 05:06:45 blog kernel: [8555931.726810] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=69.10.179.9 DST=10.10.10.5 LEN=52 TOS=0x
00 PREC=0x00 TTL=51 ID=10030 DF PROTO=TCP SPT=49197 DPT=80 WINDOW=54 RES=0x00 ACK FIN URGP=0 
Apr 21 05:06:45 blog kernel: [8555931.730049] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=69.10.179.9 DST=10.10.10.5 LEN=52 TOS=0x
00 PREC=0x00 TTL=51 ID=54079 DF PROTO=TCP SPT=47306 DPT=80 WINDOW=54 RES=0x00 ACK FIN URGP=0 
Apr 21 05:06:53 blog kernel: [8555939.888083] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=69.10.179.9 DST=10.10.10.5 LEN=52 TOS=0x
00 PREC=0x00 TTL=51 ID=10031 DF PROTO=TCP SPT=49197 DPT=80 WINDOW=54 RES=0x00 ACK FIN URGP=0 
Apr 21 05:06:53 blog kernel: [8555939.890696] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=69.10.179.9 DST=10.10.10.5 LEN=52 TOS=0x
00 PREC=0x00 TTL=51 ID=54080 DF PROTO=TCP SPT=47306 DPT=80 WINDOW=54 RES=0x00 ACK FIN URGP=0 
Apr 21 05:07:09 blog kernel: [8555956.211300] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=69.10.179.9 DST=10.10.10.5 LEN=52 TOS=0x
00 PREC=0x00 TTL=51 ID=54081 DF PROTO=TCP SPT=47306 DPT=80 WINDOW=54 RES=0x00 ACK FIN URGP=0 
Apr 21 05:47:39 blog kernel: [8558386.029451] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=69.10.179.10 DST=10.10.10.5 LEN=52 TOS=0
x00 PREC=0x00 TTL=51 ID=60315 DF PROTO=TCP SPT=34968 DPT=80 WINDOW=54 RES=0x00 ACK FIN URGP=0 
Apr 21 05:47:40 blog kernel: [8558386.686857] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=69.10.179.10 DST=10.10.10.5 LEN=52 TOS=0
x00 PREC=0x00 TTL=51 ID=42017 DF PROTO=TCP SPT=55669 DPT=80 WINDOW=54 RES=0x00 ACK FIN URGP=0 
Apr 21 05:47:40 blog kernel: [8558387.049957] [UFW BLOCK] IN=eth0 OUT= MAC=40:50:8b:02:03:05 SRC=69.10.179.10 DST=10.10.10.5 LEN=52 TOS=0
```

This doesn't seem to be causing problems -- the webserver can still be accessed -- but I'm just curious as to why this is happening. Is it something to do with the FIN and RST flags on the packets?

---

### Post by Doug S on 2013-04-25
> Is it something to do with the FIN and RST flags on the packets?Yes, it has everything to do with those flag bits. For TCP connections, Linux tends to use a "half-duplex" close sequence where either side of the session can initiate connection termination via a single 2 way FIN-ACK handshake (which puts the connection into the CLOSE_WAIT state), instead of a full 4 way FIN-ACK handshake. When one also includes routers and such, it is not uncommon, indeed common, that one side might think the connection has been terminated, while the other side thinks it has still open or not fully terminated. Your log file is, most probably, showing entries for cases where your computer thinks the tcp had been closed and it has forgotten about it, but the client is trying to close the session. In the case where you got a RST bit, it can be because the client gave up trying the FIN method and now is just trying to reset the connection. By observation only, rather than authoritative reference, it seems that Apple computers tend to use FIN and FIN-ACK more, and MS windows computers tend to use RST more.
Conclusion: Everything is fine.

---

### Post by hkphooey on 2013-04-25
Thanks Doug,
I figured it was nothing to worry about, but I'm (un)naturally curious and can't leave something like that bugging me. :-) 
Case closed ... how the frig do you mark a thread as solved? I don't have the option in Thread Tools?

---

