---
title: "ufw firewall status active but can still access port not listed in ufw status"
date: 2023-07-26
forum: General Help
---

### Post by hansmc2 on 2023-07-26
I may just be missing something but on a ubuntu box (server edition) I opened some ports and turned the firewall on, but I can still access port 5000 even though I did not open it. At least I can go to a browser and access 192.168.1.x:5000. How is that possible? 

$ [FONT=monospace][COLOR=#000000]ssh user@192.168.1.x[/COLOR][/FONT]
$ [FONT=monospace][COLOR=#000000]sudo ufw status verbose [/COLOR]
Status: active 
Logging: on (low) 
Default: deny (incoming), allow (outgoing), deny (routed) 
New profiles: skip 

To                         Action      From 
--                         ------      ---- 
22                         ALLOW IN    Anywhere                   
80                         ALLOW IN    Anywhere                   
443                        ALLOW IN    Anywhere                   
22 (v6)                    ALLOW IN    Anywhere (v6)              
80 (v6)                    ALLOW IN    Anywhere (v6)              
443 (v6)                   ALLOW IN    Anywhere (v6)  

Edit: Ubuntu server is hosting a docker container that is exposing port 5000. 
[/FONT]

---

### Post by TheFu on 2023-07-26
What is the source and destination IP address for this connection?
What do the UFW logs show?

---

### Post by hansmc2 on 2023-07-26
Source and destination IP address for this connection are both [FONT=monospace][COLOR=#000000]192.168.1.x. I will check on the logs.[/COLOR][/FONT]

---

### Post by hansmc2 on 2023-07-26
This is not what I expected to see. 

tail -f ufw.log | grep "192.168.1.s"
Jul 26 17:47:40 blue kernel: [2772966.088169] [UFW AUDIT] IN= OUT=eno1 SRC=192.168.1.d DST=192.168.1.s LEN=368 TOS=0x10 PREC=0x00 TTL=64 ID=54923 DF PROTO=TCP SPT=33126 DPT=55084 WINDOW=501 RES=0x00 ACK PSH URGP=0 
Jul 26 17:47:40 blue kernel: [2772966.092063] [UFW AUDIT] IN= OUT=eno1 SRC=192.168.1.d DST=192.168.1.s LEN=328 TOS=0x10 PREC=0x00 TTL=64 ID=54924 DF PROTO=TCP SPT=33126 DPT=55084 WINDOW=501 RES=0x00 ACK PSH URGP=0 
Jul 26 17:48:40 blue kernel: [2773026.106986] [UFW AUDIT] IN= OUT=eno1 SRC=192.168.1.d DST=192.168.1.s LEN=368 TOS=0x10 PREC=0x00 TTL=64 ID=54926 DF PROTO=TCP SPT=33126 DPT=55084 WINDOW=501 RES=0x00 ACK PSH URGP=0 
Jul 26 17:48:40 blue kernel: [2773026.108139] [UFW AUDIT] IN= OUT=eno1 SRC=192.168.1.d DST=192.168.1.s LEN=328 TOS=0x10 PREC=0x00 TTL=64 ID=54927 DF PROTO=TCP SPT=33126 DPT=55084 WINDOW=501 RES=0x00 ACK PSH URGP=0 
Jul 26 17:48:40 blue kernel: [2773026.112166] [UFW AUDIT] IN= OUT=eno1 SRC=192.168.1.d DST=192.168.1.s LEN=328 TOS=0x10 PREC=0x00 TTL=64 ID=54928 DF PROTO=TCP SPT=33126 DPT=55084 WINDOW=501 RES=0x00 ACK PSH URGP=0 

It does not seem to catch most of the activity I am expecting. The server is 192.168.1.d and the client is 192.168.1.s. The server is hosting a docker container that is exposing the port 5000. So now I am thinking that is somehow over writing the host firewall.

---

### Post by hansmc2 on 2023-07-27
Did a little more reading and I think the issue is docker. If you have a correction or something I should look into, feel free to add it but I am going to consider this solved for now. Thanks

---

### Post by TheFu on 2023-07-27
Docker should, never, ever, ever, have sshd running.  Not ever.
Additionally, if you aren't running docker in non-privileged mode, you've wasted 80% of the claimed security.  Firewalls don't work in non-privileged mode, but since docker containers are meant to run 1 service that listens on 1 port only, then it isn't a big deal.

BTW, I don't use docker due to some large security concerns. Perhaps those have been fixed, but it is too late.  Just because something is popular, that doesn't mean it is good. Docker has fantastic marketing, "meh" technology, but they did get most Linux Container managers to accept their container format.

If docker is involved, always best to mention that in the title + initial post.  Linux Containers aren't virtual machines. They have different rules, so we need to be cognizant about those differences.

---

