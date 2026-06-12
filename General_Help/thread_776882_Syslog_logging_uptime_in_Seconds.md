---
title: "Syslog logging uptime in Seconds"
date: 2008-05-01
forum: General Help
---

### Post by rolandbm on 2008-05-01
Hey All,
     I'm in the process of setting up Sawmill on our ubuntu server to track traffic from iptables but am having an issue with the way the logs are formatted. Just after the facility section it has a timestamp of the current uptime in brackets. With Sawmill it thinks this is the name of the iptable rule and gets in the way of trying to sort by traffic accepted and traffic dropped. Does anyone know a way to turn this timestamp off? I've been searching for the better part of 2 days now but am stumped. I guess the alternative would be to teach Sawmill to ignore these numbers? Any help is much appreciated.

Example Log: May  1 12:52:37 myhost kernel: [45639042.080000] [IPTABLES ACCEPT] : IN=eth0 OUT= MAC=whatever SRC=1.1.1.1 DST=2.2.2.2 LEN=46 TOS=0x00 PREC=0x00 TTL=116 ID=53672 DF PROTO=TCP SPT=1539 DPT=110 WINDOW=65424 RES=0x00 ACK PSH URGP=0

Sawmill thinks "[45639042.080000] [IPTABLES ACCEPT]" is the rule name. Thanks!

Brad

---

