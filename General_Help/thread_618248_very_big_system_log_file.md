---
title: "very big system log file"
date: 2007-11-20
forum: General Help
---

### Post by Biochem on 2007-11-20
I wok up this morning and my / filesystem was full. After some investigation I found that the culprits were 3 files (1.2Gig each). here is a small sample of each files.

Can someone help me find what causes the problem. I've also attached the last 1000 line of each the log files.

/var/log/kern.log
> Nov 20 03:25:30 nefuats kernel: [668144.979931] Inbound IN=ppp0 OUT= MAC= SRC=132.204.85.205 DST=208.111.95.211 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=5008 DF PROTO=TCP SPT=56830 DPT=25 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 20 03:25:30 nefuats kernel: [668144.980170] Inbound IN=ppp0 OUT= MAC= SRC=132.204.85.205 DST=208.111.95.211 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=21402 DF PROTO=TCP SPT=56831 DPT=25 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 20 03:25:30 nefuats kernel: [668144.980485] Inbound IN=ppp0 OUT= MAC= SRC=132.204.85.205 DST=208.111.95.211 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=30904 DF PROTO=TCP SPT=56832 DPT=25 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 20 03:25:30 nefuats kernel: [668144.980736] Inbound IN=ppp0 OUT= MAC= SRC=132.204.85.205 DST=208.111.95.211 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=17357 DF PROTO=TCP SPT=56833 DPT=25 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 20 03:27:38 nefuats kernel: [668272.595423] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=7726 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:27:39 nefuats kernel: [668273.340513] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=7728 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:27:40 nefuats kernel: [668274.089024] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=7730 PROTO=UDP SPT=137 DPT=137 LEN=58 

/var/log/messages
> Nov 20 03:52:13 nefuats kernel: [669744.631922] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=8483 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:52:14 nefuats kernel: [669745.380268] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=8485 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:53:53 nefuats kernel: [669844.702384] Inbound IN=ppp0 OUT= MAC= SRC=24.64.125.65 DST=208.111.95.211 LEN=512 TOS=0x00 PREC=0x00 TTL=69 ID=15074 PROTO=UDP SPT=10122 DPT=1026 LEN=492 
Nov 20 03:53:53 nefuats kernel: [669844.703323] Inbound IN=ppp0 OUT= MAC= SRC=24.64.125.65 DST=208.111.95.211 LEN=512 TOS=0x00 PREC=0x00 TTL=69 ID=15075 PROTO=UDP SPT=10122 DPT=1027 LEN=492 
Nov 20 03:53:53 nefuats kernel: [669844.704305] Inbound IN=ppp0 OUT= MAC= SRC=24.64.125.65 DST=208.111.95.211 LEN=512 TOS=0x00 PREC=0x00 TTL=69 ID=15076 PROTO=UDP SPT=10122 DPT=1028 LEN=492 
Nov 20 03:54:24 nefuats kernel: [669875.143216] Unknown OutputIN= OUT=tap0 SRC=10.8.0.1 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:54:24 nefuats kernel: [669875.143240] Unknown InputIN=tap0 OUT= MAC= SRC=10.8.0.1 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:54:24 nefuats kernel: [669875.161653] Unknown InputIN=tap0 OUT= MAC=00:ff:f6:f6:8f:74:00:ff:11:14:27:68:08:00 SRC=10.8.0.2 DST=10.8.0.1 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
Nov 20 03:54:43 nefuats kernel: [669894.770528] Inbound IN=ppp0 OUT= MAC= SRC=124.210.172.87 DST=208.111.95.211 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=28662 PROTO=TCP SPT=1167 DPT=135 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov 20 03:55:12 nefuats kernel: [669923.061687] Inbound IN=ppp0 OUT= MAC= SRC=132.204.85.205 DST=208.111.95.211 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=55929 DF PROTO=TCP SPT=50994 DPT=25 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 20 03:55:15 nefuats kernel: [669926.054170] Inbound IN=ppp0 OUT= MAC= SRC=132.204.85.205 DST=208.111.95.211 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=55930 DF PROTO=TCP SPT=50994 DPT=25 WINDOW=5840 RES=0x00 SYN URGP=0 

/var/log/syslog
> Nov 20 03:51:58 nefuats kernel: [669729.690783] Unknown OutputIN= OUT=tap0 SRC=10.8.0.1 DST=10.8.0.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
Nov 20 03:51:58 nefuats kernel: [669729.690804] Unknown InputIN=tap0 OUT= MAC= SRC=10.8.0.1 DST=10.8.0.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
Nov 20 03:52:05 nefuats kernel: [669737.148174] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=8471 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:52:06 nefuats kernel: [669737.893950] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=8473 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:52:07 nefuats kernel: [669738.642757] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=8475 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 20 03:52:12 nefuats kernel: [669743.883870] Unknown InputIN=tap0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:ff:b1:bb:11:e7:08:00 SRC=10.8.0.3 DST=10.8.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=8481 PROTO=UDP SPT=137 DPT=137 LEN=58 

The timestamps of the first line is November 18. 

thank you

---

### Post by cmnorton on 2007-11-20
Sorry that this is not an answer, but a pointer. I started Googling "Inbound IN=" and came up with a lot of hits that point, among many things, to firestarter and vpn connections. What is your system set up to do and what kind of network connection do you have?

---

### Post by rmemm on 2007-11-20
I'm not quite sure -- to me they look to be network firewall or routing messages.

I would look at the IP addresses and port numbers of these and try to figure out what were the source and destination addresses and ports.

For example -- looks like some of these are related to your PPP connection -- I'm assuming you are using PPP to connect to the network?  

Some of the TCP packets look like they are going to port 25 which is usally SMTP.  Do you normally recieve mail usings SMTP?  If not -- this is quite strange.

There is some UDP traffice on port 137 which is NETBIOS typically used by MS Windows.  Seems like there must be an MS Windows machine around or elase you have Samba installed somewhere?

Other thing I would say -- this many messages -- seems to me like either some link or device is failing or going UP and DOWN or it's some sort of malware -- like a virus or worm on your LAN somewhere.  It's got to be something that is send a lot of packets that are not normal.

Maybe close down your PPP conection and see if it goes away -- or if you have other computers on your net shut them off if you can and see if it goes away.  There is also a tool called Ethereal (or now called Wireshark) that can look at packets in more detail.

Rob

---

### Post by Biochem on 2007-11-21
Thanks for the input.

After having a second look it seems like the problem comes from my openvpn server (tap0) and in many ppp0 entries I recognize the IP as being from my university where the clients are. Closing the server stops the tap0 entries. I will have to look at my server configuration maybe those keep connection alive setting are not well set.

---

