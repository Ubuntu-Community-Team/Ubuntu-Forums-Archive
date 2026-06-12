---
title: "Log IPTABLES output to seperate log file?"
date: 2006-08-09
forum: General Help
---

### Post by Daniel15 on 2006-08-09
Hi,
 I recently set up an IPTABLES-based firewall as according to the [Linux IP Masquerading HOWTO](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/) (and managed to get it working alongside MoBlock). This is all working well, except for one problem: All the firewall hits are being logged into the standard system log. Running 'dmesg' would produce output similar to:
```

[......]
[343879.173477] IN=ppp0 OUT= MAC= SRC=220.245.171.226 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=19451 DF PROTO=TCP SPT=4089 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0
[343957.435262] IN=ppp0 OUT= MAC= SRC=220.245.153.69 DST=220.245.134.86 LEN=64 TOS=0x00 PREC=0x00 TTL=47 ID=33994 DF PROTO=TCP SPT=2809 DPT=445 WINDOW=53760 RES=0x00 SYN URGP=0
[343960.406722] IN=ppp0 OUT= MAC= SRC=220.245.153.69 DST=220.245.134.86 LEN=64 TOS=0x00 PREC=0x00 TTL=47 ID=34351 DF PROTO=TCP SPT=2809 DPT=445 WINDOW=53760 RES=0x00 SYN URGP=0
[344091.673192] IN=ppp0 OUT= MAC= SRC=220.245.171.226 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=54458 DF PROTO=TCP SPT=3461 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0
[344094.558716] IN=ppp0 OUT= MAC= SRC=220.245.171.226 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=54927 DF PROTO=TCP SPT=3461 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0
[344177.589783] IN=ppp0 OUT= MAC= SRC=220.245.145.96 DST=220.245.134.86 LEN=64 TOS=0x00 PREC=0x00 TTL=48 ID=56559 DF PROTO=TCP SPT=1733 DPT=445 WINDOW=53760 RES=0x00 SYN URGP=0
[......]

```

Likewise, running 'sudo tail /var/log/messages' yields:
```

daniel@server1:~$ sudo tail /var/log/messages
[......]
Aug  9 21:11:08 server1 kernel: [343957.435262] IN=ppp0 OUT= MAC= SRC=220.245.153.69 DST=220.245.134.86 LEN=64 TOS=0x00 PREC=0x00 TTL=47 ID=33994 DF PROTO=TCP SPT=2809 DPT=445 WINDOW=53760 RES=0x00 SYN URGP=0
Aug  9 21:11:11 server1 kernel: [343960.406722] IN=ppp0 OUT= MAC= SRC=220.245.153.69 DST=220.245.134.86 LEN=64 TOS=0x00 PREC=0x00 TTL=47 ID=34351 DF PROTO=TCP SPT=2809 DPT=445 WINDOW=53760 RES=0x00 SYN URGP=0
Aug  9 21:13:22 server1 kernel: [344091.673192] IN=ppp0 OUT= MAC= SRC=220.245.171.226 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=54458 DF PROTO=TCP SPT=3461 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0
Aug  9 21:13:25 server1 kernel: [344094.558716] IN=ppp0 OUT= MAC= SRC=220.245.171.226 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=54927 DF PROTO=TCP SPT=3461 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0
Aug  9 21:14:48 server1 kernel: [344177.589783] IN=ppp0 OUT= MAC= SRC=220.245.145.96 DST=220.245.134.86 LEN=64 TOS=0x00 PREC=0x00 TTL=48 ID=56559 DF PROTO=TCP SPT=1733 DPT=445 WINDOW=53760 RES=0x00 SYN URGP=0
Aug  9 21:14:51 server1 kernel: [344180.308286] IN=ppp0 OUT= MAC= SRC=220.245.145.96 DST=220.245.134.86 LEN=64 TOS=0x00 PREC=0x00 TTL=48 ID=56957 DF PROTO=TCP SPT=1733 DPT=445 WINDOW=53760 RES=0x00 SYN URGP=0
Aug  9 21:15:00 server1 kernel: [344189.489367] IN=ppp0 OUT= MAC= SRC=220.245.149.54 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=63303 DF PROTO=TCP SPT=3498 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0
Aug  9 21:15:04 server1 kernel: [344192.637910] IN=ppp0 OUT= MAC= SRC=220.245.149.54 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=63899 DF PROTO=TCP SPT=3498 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=16896
Aug  9 21:15:34 server1 kernel: [344222.691957] IN=ppp0 OUT= MAC= SRC=220.245.182.81 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=10217 DF PROTO=TCP SPT=2602 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0
Aug  9 21:15:36 server1 kernel: [344225.564898] IN=ppp0 OUT= MAC= SRC=220.245.182.81 DST=220.245.134.86 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=10390 DF PROTO=TCP SPT=2602 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0
[......]

```
And the same for /var/log/syslog... Now, while I want these hits to be logged, I don't like them being written to the standard log files. Is there a way to redirect these messages to a seperate file (maybe /var/log/firewall) and keep them out of these log files?

Thanks in advance,
 --Daniel15

---

### Post by mannheim on 2006-08-09
In your iptables configuration, logging is specified by using the "LOG" target. Instead, you can use the target "ULOG", but first you need to install the ulogd daemon (apt-get install ulogd).

The options for the ULOGD target in iptables are listed [here]("http://iptables-tutorial.frozentux.net/chunkyhtml/x4883.html").

I think something like this is supposed to work: add an iptables rule like
```
iptables -A INPUT -j ULOG --ulog-nlgroup 1
```

Then edit /etc/ulogd.conf to specify the destination file for you log messages by editing the line under the [LOGEMU] heading.

EDIT: I just checked that "1" is the default for --ulog-nlgroup, so the iptables rule above can be shortened.

---

