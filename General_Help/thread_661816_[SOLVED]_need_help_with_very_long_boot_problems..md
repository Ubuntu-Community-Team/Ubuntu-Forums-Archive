---
title: "[SOLVED] need help with very long boot problems."
date: 2008-01-08
forum: General Help
---

### Post by Omnios on 2008-01-08
K story so far I have a P4 1.6 ghz that I had Windows and Ubuntu 7.10 on. My dad had the exact same box and motherboard cpu etc. Anyways I canebalized my old box and put everything into the box I got from my dad. The only big differences are that I took the 256megs ram from my old tower and put it into the one I got so I have 512megs ram now.Also I replaced a secondary 40G drive with a 80G drive. I had a lot of problems with the partitions but got sorted out ok. 

 Now the problem I am having is it boots and the splash screen shows up ok but as the bar loads it hangs at varios places for a very long time. Also at the end of the dmesg I got this which is worrying.

 ```
requested_mask="a" denied_mask="a" name="/dev/tty" pid=6848 profile="/usr/sbin/cupsd"
[  195.478409] Failure registering capabilities with primary security module.
[53832.328510] Inbound IN=eth0 OUT= MAC=00:80:c6:f1:a3:3e:00:04:e2:93:01:76:08:00 SRC=82.77.237.95 DST=192.168.2.192 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=61726 DF PROTO=TCP SPT=6990 DPT=53537 WINDOW=65535 RES=0x00 ACK URGP=0 
[53833.333498] Inbound IN=eth0 OUT= MAC=00:80:c6:f1:a3:3e:00:04:e2:93:01:76:08:00 SRC=82.77.237.95 DST=192.168.2.192 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=61750 DF PROTO=TCP SPT=6990 DPT=53537 WINDOW=65535 RES=0x00 ACK URGP=0 
[53834.308962] Inbound IN=eth0 OUT= MAC=00:80:c6:f1:a3:3e:00:04:e2:93:01:76:08:00 SRC=82.77.237.95 DST=192.168.2.192 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=61764 DF PROTO=TCP SPT=6990 DPT=53537 WINDOW=65535 RES=0x00 ACK URGP=0 
[53835.479706] Inbound IN=eth0 OUT= MAC=00:80:c6:f1:a3:3e:00:04:e2:93:01:76:08:00 SRC=82.77.237.95 DST=192.168.2.192 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=61784 DF PROTO=TCP SPT=6990 DPT=53537 WINDOW=65535 RES=0x00 ACK URGP=0 
[53836.493067] Inbound IN=eth0 OUT= MAC=00:80:c6:f1:a3:3e:00:04:e2:93:01:76:08:00 SRC=82.77.237.95 DST=192.168.2.192 LEN=41 TOS=0x00 PREC=0x00 TTL=114 ID=61812 DF PROTO=TCP SPT=6990 DPT=53537 WINDOW=65535 RES=0x00 ACK URGP=0 
tom@mio:~$ 


```

 The boot probably has to do with network stuff.

---

### Post by Omnios on 2008-03-29
K problem solved it was not the hard drive.
 
 I tried the GNU/Hurd live cd (no Gui) and it had boot areas. So after unplugging the hard drive I found it was not that so after some problem solving and thinking I unpluged a old cdrw I had in the old tower. Anyways the hurd live cd worked. So I left it unpluged and booted Ubunt and shure anouph my boot is now normal. 
 
 This brings me to thin a lot of slow bot problems may be caused by older cheap cd roms.

---

