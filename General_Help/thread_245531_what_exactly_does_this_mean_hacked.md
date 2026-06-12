---
title: "what exactly does this mean? hacked?"
date: 2006-08-28
forum: General Help
---

### Post by xinix on 2006-08-28
There are about 35 entries like this in a 30 second time frame entry in my system.log:```
[17183123.104000] Inbound IN=eth0 OUT= MAC=00:e0:4c:e0:02:72:00:0f:b5:ac:68:84:08:00 SRC=213.115.162.29 DST=192.168.1.2 LEN=68 TOS=0x10 PREC=0x60 TTL=50 ID=57845 PROTO=ICMP TYPE=3 CODE=10 [SRC=192.168.1.2 DST=213.115.162.29 LEN=40 TOS=0x10 PREC=0x60 TTL=50 ID=57844 DF PROTO=TCP SPT=42292 DPT=80 WINDOW=11680 RES=0x00 ACK FIN URGP=0 ]
``` 

There are also a whole bunch of entries like this:
```
[17188481.716000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
```


thanks

---

### Post by kerry_s on 2006-08-28
Well, the first one is a connectiont to the mysql web site here-> [http://213.115.162.29/](http://213.115.162.29/)

The other 2 are keyboard related, it saying you pressed a key it don't reconize.

---

### Post by xinix on 2006-08-28
Awesome, thanks. I find it interesting that I don't get a similar entry when I connect to other sites. I guess that's why I thought there might have been something else going on.  That, and I didn't understand the nature of the connection.  Only that I had established one.

After posting I was able to search for the second set of errors.  It seems to be related to pressing two keys at once.  Odd that I started getting it after I went to the mysql site.

Does anyone know why this site would seem to leave a unique footprint like that?

---

