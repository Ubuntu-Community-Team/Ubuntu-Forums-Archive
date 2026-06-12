---
title: "What do these lines in /var/log/syslog mean?"
date: 2014-04-18
forum: General Help
---

### Post by vasa1 on 2014-04-18
Excerpt from */var/log/syslog*
```
Apr 18 09:39:09 vasa1-Inspiron-1545 kernel: [ 8788.085830] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=1.9.69.196 DST=115.69.251.79 LEN=44 TOS=0x00 PREC=0x00 TTL=120 ID=48138 PROTO=UDP SPT=10753 DPT=16464 LEN=24 
Apr 18 09:39:32 vasa1-Inspiron-1545 kernel: [ 8810.807048] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=88.165.235.22 DST=115.69.251.79 LEN=129 TOS=0x08 PREC=0x20 TTL=49 ID=24110 PROTO=UDP SPT=16001 DPT=48220 LEN=109 
Apr 18 09:39:49 vasa1-Inspiron-1545 kernel: [ 8828.576267] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=88.165.235.22 DST=115.69.251.79 LEN=129 TOS=0x08 PREC=0x20 TTL=49 ID=24114 PROTO=UDP SPT=16001 DPT=48220 LEN=109 
Apr 18 09:40:09 vasa1-Inspiron-1545 kernel: [ 8848.075010] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=88.165.235.22 DST=115.69.251.79 LEN=129 TOS=0x08 PREC=0x20 TTL=49 ID=24118 PROTO=UDP SPT=16001 DPT=48220 LEN=109 
Apr 18 09:40:58 vasa1-Inspiron-1545 kernel: [ 8897.190475] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=88.165.235.22 DST=115.69.251.79 LEN=129 TOS=0x08 PREC=0x20 TTL=49 ID=24124 PROTO=UDP SPT=16001 DPT=48220 LEN=109 
Apr 18 09:40:59 vasa1-Inspiron-1545 kernel: [ 8898.017542] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=88.165.235.22 DST=115.69.251.79 LEN=129 TOS=0x08 PREC=0x20 TTL=49 ID=24125 PROTO=UDP SPT=16001 DPT=48220 LEN=109 
Apr 18 09:41:13 vasa1-Inspiron-1545 kernel: [ 8912.765962] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=88.220.188.11 DST=115.69.251.79 LEN=131 TOS=0x00 PREC=0x00 TTL=119 ID=4939 PROTO=UDP SPT=55999 DPT=48220 LEN=111 
Apr 18 09:41:33 vasa1-Inspiron-1545 kernel: [ 8931.928264] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=180.97.152.7 DST=115.69.251.79 LEN=129 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=20406 DPT=48220 LEN=109 
Apr 18 09:41:49 vasa1-Inspiron-1545 kernel: [ 8948.448972] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=121.54.44.88 DST=115.69.251.79 LEN=129 TOS=0x00 PREC=0x00 TTL=43 ID=19745 PROTO=UDP SPT=39507 DPT=48220 LEN=109 

```
I don't remember seeing them in 13.10.
My system is Lubuntu 14.04 with ufw enabled. All I've done re. ufw is this:
```
**sudo ufw status**
sudo password for vasa1:
Status: inactive
**sudo ufw enable**
Firewall is active and enabled on system startup
**sudo ufw default deny**
Default incoming policy changed to 'deny`
(be sure to update your rules accordingly)

```
I haven't done anything at all to *iptables* or anything else firewall-related. My ISP is the same as before when I didn't see all these messages.

---

