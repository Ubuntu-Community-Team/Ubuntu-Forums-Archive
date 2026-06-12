---
title: "Problem After Connecting to Internet"
date: 2007-01-04
forum: General Help
---

### Post by irix on 2007-01-04
Hi all,
I have a problem after connecting to Internet in ubuntu. I don't know what I have changed that cause this problem. After a successful connection it seems not work and could not handle the data received. Just the last lines repeat and repeat in my log file! Take a look:

```
root@Persia:/home/irix# pon dsl-provider
Plugin rp-pppoe.so loaded.

root@Persia:/home/irix# plog
Jan 4 18:58:56 Persia pppd[5391]: peer from calling number 00:0C:29:AB:A7:B3 authorized
Jan 4 18:58:56 Persia pppd[5391]: replacing old default route to eth0 [192.168.16.1]
Jan 4 18:58:56 Persia pppd[5391]: Cannot determine ethernet address for proxy ARP
Jan 4 18:58:56 Persia pppd[5391]: local IP address 10.10.10.4
Jan 4 18:58:56 Persia pppd[5391]: remote IP address 10.0.0.100
Jan 4 18:58:56 Persia pppd[5391]: primary DNS address 217.218.195.19
Jan 4 18:58:56 Persia pppd[5391]: secondary DNS address 217.218.195.20
Jan 4 18:58:56 Persia pppd[5391]: CCP terminated by peer (No compression negotiated)
Jan 4 18:58:56 Persia pppd[5391]: Compression disabled by peer.

root@Persia:/home/irix# ping yahoo.com
ping: unknown host yahoo.com

root@Persia:/home/irix# tail /var/log/messages
Jan 4 18:59:08 Persia kernel: [17179833.568000] Unknown OutputIN= OUT=ppp0 SRC=10.10.10.4 DST=217.218.195.20 LEN=55 TOS=0x00 PREC=0x00 TTL=64 ID=56632 DF PROTO=UDP SPT=1027 DPT=53 LEN=35
Jan 4 18:59:08 Persia kernel: [17179833.568000] Unknown OutputIN= OUT=ppp0 SRC=10.10.10.4 DST=217.218.195.19 LEN=55 TOS=0x00 PREC=0x00 TTL=64 ID=56632 DF PROTO=UDP SPT=1027 DPT=53 LEN=35
Jan 4 18:59:08 Persia kernel: [17179833.568000] Unknown OutputIN= OUT=ppp0 SRC=10.10.10.4 DST=217.218.195.20 LEN=55 TOS=0x00 PREC=0x00 TTL=64 ID=56632 DF PROTO=UDP SPT=1027 DPT=53 LEN=35
Jan 4 18:59:10 Persia kernel: [17179835.384000] Unknown OutputIN= OUT=ppp0 SRC=10.10.10.4 DST=85.214.73.63 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=64283 DF PROTO=TCP SPT=2392 DPT=9001 WINDOW=5792 RES=0x00 SYN URGP=0
```
Any idea?

---

### Post by irix on 2007-01-05
Any help?

---

