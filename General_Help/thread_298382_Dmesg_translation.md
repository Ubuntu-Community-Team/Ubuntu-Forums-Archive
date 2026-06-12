---
title: "Dmesg translation"
date: 2006-11-12
forum: General Help
---

### Post by m2006h on 2006-11-12
I noticed about seven pages of recurring requests that are shown in dmesg. Here is a small sample:

[INDENT]
[26472.012289] Inbound IN=eth0 OUT= MAC=00:03:6d:18:d3:1a:00:06:25:86:2a:7f:08:00 SRC=63.247.132.88 DST=192.168.1.100 LEN=1500 TOS=0x00 PREC=0x20 TTL=50 ID=50362 DF PROTO=TCP SPT=2082 DPT=54665 WINDOW=6432 RES=0x00 ACK URGP=0 
[26509.109519] Inbound IN=eth0 OUT= MAC=00:03:6d:18:d3:1a:00:06:25:86:2a:7f:08:00 SRC=63.247.132.88 DST=192.168.1.100 LEN=1500 TOS=0x00 PREC=0x20 TTL=50 ID=50363 DF PROTO=TCP SPT=2082 DPT=54665 WINDOW=6432 RES=0x00 ACK URGP=0 
[26726.875197] Inbound IN=eth0 OUT= MAC=00:03:6d:18:d3:1a:00:06:25:86:2a:7f:08:00 SRC=63.247.135.2 DST=192.168.1.100 LEN=1019 TOS=0x00 PREC=0x20 TTL=50 ID=23002 DF PROTO=TCP SPT=80 DPT=54684 WINDOW=10875 RES=0x00 ACK PSH URGP=0 
[26762.699907] Inbound IN=eth0 OUT= MAC=00:03:6d:18:d3:1a:00:06:25:86:2a:7f:08:00 SRC=63.247.135.2 DST=192.168.1.100 LEN=1019 TOS=0x00 PREC=0x20 TTL=50 ID=23003 DF PROTO=TCP SPT=80 DPT=54684 WINDOW=10875 RES=0x00 ACK PSH URGP=0 
[32993.066537] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:03:93:b6:4b:36:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=124 TOS=0x00 PREC=0x00 TTL=64 ID=29229 PROTO=UDP SPT=55447 DPT=2222 LEN=104 
[32997.872820] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:03:93:b6:4b:36:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=34 TOS=0x00 PREC=0x00 TTL=64 ID=29234 PROTO=UDP SPT=55448 DPT=2222 LEN=14 [/INDENT]

I have two other boxes behind this one, which is the gateway, but neither boot log shows anything like this. The 192.168.1.100 is the default Lynksis.

Looks like someone is trying to get in. Can anyone help me to understand what is happening?

---

### Post by DaveBorealis on 2006-11-12
Looks to me like normal DNS traffic between your router (192.168.1.100) and the DNS server.

Dave

---

### Post by m2006h on 2006-11-12
That's good news! I just wasn't expecting that sort of thing in the boot log.

Thanks!

---

### Post by DaveBorealis on 2006-11-12
I just did a ```
whois 63.247.132.88
``` which returned a DNS service.

And '192.168.0.3' is your machine's IP?

BTW, someone trying to get in is also normal traffic.  Keep your software up to date (avoiding vulnerabilites), and use your router's firewall and the iptables firewall on your machine should keep things safe.

---

### Post by m2006h on 2006-11-13
Yes, that is one of the computers on my network. From the lynksys I have a Ubuntu box (192.168.0.2, a gateway with some others behind it), but I also have a notebook directly into the lynksys (the 192.168.0.3 IP) in case the gateway is down for some reason.

---

