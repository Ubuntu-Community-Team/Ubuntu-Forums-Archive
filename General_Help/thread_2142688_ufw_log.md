---
title: "ufw log"
date: 2013-05-06
forum: General Help
---

### Post by Peter1981 on 2013-05-06
Hi,

I have these lines in the syslog file many times.

May  2 06:34:14 ubuntu dhclient: DHCPREQUEST of 192.168.0.8 on eth0 to 192.168.0.1 port 67
May  2 06:34:14 ubuntu dhclient: send_packet: Operation not permitted
May  2 06:34:14 ubuntu kernel: [150052.415335] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.0.8 DST=192.168.0.1 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=68 DPT=67 LEN=308  

The SRC address is the IP address of my server and the DST address is the router IP address(I mean this is the address I can reach reach the router if I want to do something with it).

And I have these lines in the ufw.log file many times.

Apr 21 23:54:23 ubuntu kernel: [103651.693066] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.0.8 DST=192.168.0.1 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=68 DPT=67 LEN=308

These lines appear in every 5-20 seconds.
If I connect to my server or anybody these line just disappear for a while. And if you disconnect everything starts from the beginning.

What can I do with this?
The serves works properly anyway.

Thank you

Peter

---

