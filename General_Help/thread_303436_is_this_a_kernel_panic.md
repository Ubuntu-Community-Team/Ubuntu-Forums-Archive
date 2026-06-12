---
title: "is this a kernel panic?"
date: 2006-11-20
forum: General Help
---

### Post by huggy77 on 2006-11-20
i am trying to work on my log files - make sure i know whats going on in the box--  i have the below errors all over.. 


[43189310.050000] Inbound IN=eth0 OUT= MAC=00:17:08:58:a7:bc:00:0f:8f:60:bb:96:08:00 SRC=24.64.123.177 DST=10.10.10.62 LEN=512 TOS=0x00 PREC=0x00 TTL=66 ID=45587 PROTO=UDP SPT=32378 DPT=1026 LEN=492 

i am using ksystem log-is that a good log program?

---

### Post by dcstar on 2006-11-21
> **huggy77 said:**
> i am trying to work on my log files - make sure i know whats going on in the box--  i have the below errors all over.. 


[43189310.050000] Inbound IN=eth0 OUT= MAC=00:17:08:58:a7:bc:00:0f:8f:60:bb:96:08:00 SRC=24.64.123.177 DST=10.10.10.62 LEN=512 TOS=0x00 PREC=0x00 TTL=66 ID=45587 PROTO=UDP SPT=32378 DPT=1026 LEN=492 


It is a message that something at IP address 24.64.123.177 tried to contact 10.10.10.62 via UDP to port 1026.

You must decide if it is important or not.

---

### Post by huggy77 on 2006-11-22
NOT important - i am getting porscanned but i have my firewall up....

---

