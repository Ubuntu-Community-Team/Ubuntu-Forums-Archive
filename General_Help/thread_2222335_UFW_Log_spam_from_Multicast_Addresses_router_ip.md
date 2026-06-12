---
title: "UFW Log spam from Multicast Addresses router ip?"
date: 2014-05-06
forum: General Help
---

### Post by Psil0cybin on 2014-05-06
To start off, I am very new to using UFW. I have googled, but want to find out what is the 'correct' procedure for fixing this issue.

Taking a look at my UFW Log, I saw the following;

```
May  5 20:10:29 JohnExample kernel: [ 4260.446824] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  5 20:12:33 JohnExample kernel: [ 4384.866217] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  5 20:14:38 JohnExample kernel: [ 4509.387987] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  5 20:16:42 JohnExample kernel: [ 4633.909661] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  5 20:18:47 JohnExample kernel: [ 4758.431659] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  5 20:20:51 JohnExample kernel: [ 4882.851082] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  5 20:22:56 JohnExample kernel: [ 5007.372906] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:17:44 JohnExample kernel: [  137.023041] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:19:49 JohnExample kernel: [  261.484088] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:21:53 JohnExample kernel: [  385.942412] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:23:58 JohnExample kernel: [  510.299676] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:26:02 JohnExample kernel: [  634.761015] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:28:07 JohnExample kernel: [  759.282891] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:30:11 JohnExample kernel: [  883.804711] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:32:15 JohnExample kernel: [  104.873410] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:34:20 JohnExample kernel: [  229.456259] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:36:24 JohnExample kernel: [  354.038956] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:38:29 JohnExample kernel: [  478.622908] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:40:33 JohnExample kernel: [  603.104537] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  6 02:42:38 JohnExample kernel: [  727.688636] [UFW BLOCK] IN=wlan0 OUT= MAC=01:t2:k8:0z:00:21:d8:6h:x7:23:04:nbb:01:22 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 

```

do I set a rule around what is happening? I want to keep logging set, everything is at the default setting at the moment. ( I am very glad to see UFW working, hard)
Thanks for your help and suggestions guys!

---

### Post by ddreamer on 2014-06-06
The log means ufw block of multicast from 192.168.2.1 according to default policy (deny all incoming and allow all outgoing). To stop such logs, you should set up a deny (or allow) rule explicitly:

#sudo ufw deny from 192.168.2.1

---

