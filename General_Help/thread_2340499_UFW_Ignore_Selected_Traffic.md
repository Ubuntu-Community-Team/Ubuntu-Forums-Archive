---
title: "UFW Ignore Selected Traffic"
date: 2016-10-19
forum: General Help
---

### Post by SageOfSmeg on 2016-10-19
I have "ufw logging on" but would like to ignore (not log/report) specific traffic, i.e.
 
```
kernel: [35304.642248] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1d:aa:dc:5d:c0:08:00 SRC=192.168.1.43 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=2762 PROTO=2
```

192.168.1.43 is my router gateway and I wish to ignore the 224.0.0.1 entry.
 
Is there a way to allow and ignore at the same time?

---

