---
title: "[SOLVED] External USB HDD Sense?"
date: 2008-01-15
forum: General Help
---

### Post by devnulljp on 2008-01-15
My external USB HDD has started acting up. I suspect it's preparing to die. But, I've noticed some weird errors in dmesg whenever I turn it on: 
It starts off straightforward enough with info on sectors, cache etc. but then it starts into something that looks like network errors? It goes on like that for a while. Any ideas? Why would plugging in a hard drive result in network activity?  

[ 6227.112000] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 6227.112000] sd 3:0:0:0: [sdb] Write Protect is off
[ 6227.112000] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 6227.112000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 6227.112000] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 6227.116000] sd 3:0:0:0: [sdb] Write Protect is off
[ 6227.116000] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 6227.116000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 6227.116000]  sdb: sdb1 < sdb5 sdb6 >
[ 6227.160000] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 6227.160000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[B][ 6229.320000] PUB_IN DROP 4 IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=87.239.6.22 DST=192.168.1.2 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=16800 PROTO=TCP SPT=23832 DPT=49420 WINDOW=0 RES=0x00 RST URGP=0 
[ 6229.320000] PUB_IN DROP 4 IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=151.71.215.100 DST=192.168.1.2 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=23220 PROTO=TCP SPT=25152 DPT=52633 WINDOW=0 RES=0x00 RST URGP=0 
[ 6229.320000] PUB_IN DROP 4 IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=172.189.167.210 DST=192.168.1.2 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=19489 PROTO=TCP SPT=25786 DPT=45138 WINDOW=0 RES=0x00 RST URGP=0 
[ 6229.320000] PUB_IN DROP 4 IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=172.189.167.210 DST=192.168.1.2 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=30336 PROTO=TCP SPT=25786 DPT=45137 WINDOW=0 RES=0x00 RST URGP=0 
[ 6229.320000] PUB_IN DROP 4 IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=172.189.167.210 DST=192.168.1.2 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=26104 PROTO=TCP SPT=25786 DPT=45134 WINDOW=0 RES=0x00 RST URGP=0 
[/B]

---

### Post by Het Irv on 2008-01-15
Is there anything on the Drive that is tring to connect to the Internet?  Programs that are trying to Update?

---

