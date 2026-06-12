---
title: "Find process on my machine writing to port on another machine?"
date: 2020-09-21
forum: General Help
---

### Post by MgFrobozz on 2020-09-21
Looking at dmesg today, I noticed that I've got a process attempting to write to ports 139 and 445 on another machine, reported by whois as akamai.com

> 
[Mon Sep 21 10:57:53 2020] IN= OUT=enp7s0 SRC=192.168.0.2 DST=198.105.254.23 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=25947 DF PROTO=TCP SPT=58764 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 
[Mon Sep 21 10:57:53 2020] IN= OUT=enp7s0 SRC=192.168.0.2 DST=198.105.254.23 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=47830 DF PROTO=TCP SPT=40330 DPT=139 WINDOW=64240 RES=0x00 SYN URGP=0 


Those are reports from iptables, which I've set to disallow those accesses.I know how to track down what processes are listening to another port on my machine, but not how to track down who's writing to ports 139 and 445 on akamai. I'm concerned that I've picked up some sort of bot/virus.

Thanks for any help.

---

### Post by yapidumoac on 2020-09-21
netstat -ltnp | grep -w ':139'
netstat -ltnp | grep -w ':445'

---

### Post by HermanAB on 2020-09-22
It means that you are running a Windows networking system such as Samba.

---

### Post by MgFrobozz on 2020-09-26
HermanAB, I'm running ubuntu 18.04 LTS (linux). But I think you're correct about the port 445 tries: /etc/services reports 445 is "Microsoft Naked CIFS", and I think the process is attempting to access a CIFS server at akamai.com. I'm wondering whether this is a bot/virus.

It's stopped trying, for now, but I'll use yapidumoac's netstat command if it starts up again.

---

### Post by MgFrobozz on 2020-09-26
yapidumoac, it's stopped for now, but I'll try this when it starts up again (which it did yesterday).

---

