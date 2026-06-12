---
title: "ufw inactive after short time"
date: 2012-10-14
forum: General Help
---

### Post by p3tter on 2012-10-14
hello i have ufw running on my ubuntu 12.04LTS server and the ufw goes inactive after a short time, even i use sudo ufw enable, and set the ufw to run from startup. how could i fix this? i want my firewall active 24/7!
thanks

---

### Post by Doug S on 2012-10-14
Hi and welcome to Ubuntu forums.
I do not use ufw, so I don't know for sure, but...
ufw only needs to make an iptables rule set, then it wouldn't have anything left to do, so perhaps it terminates. If you want to check ou the status of your firewall try this:```
sudo iptables -v -x -n -L
```or this:```
sudo iptables-save -c
```

---

### Post by p3tter on 2012-10-14
my ufw chain not showing in iptables, my second firewall dome9 security chain shows, after i start ufw again, the ufw chain appear in iptables.

---

### Post by Doug S on 2012-10-14
Hopefully someone that actually uses ufw will join this thread and help you.
In the meantime, do you get any clues from any of the log files in /var/log? I am thinking of /var/log/ufw.log or kern.log or syslog or other.

---

### Post by p3tter on 2012-10-14
here is som of the last lines from my ufw log:


Oct 14 23:56:02 media2 kernel: [26275.776228] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:6e62:6dff:fee0:df01 DST=fe80:0000:0000:0000:1240:f3ff:fe7b:3a84 LEN=78 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=6881 DPT=6$

Oct 14 23:56:05 media2 kernel: [26278.785304] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:6e62:6dff:fee0:df01 DST=fe80:0000:0000:0000:1240:f3ff:fe7b:3a84 LEN=78 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=6881 DPT=6$

from oct 14 23:56:05 is the time my ufw got inactive again, i took this log at Oct 15 00:05
so its stop working completely after 23:56 o"clock

this line is from my syslog: same time stamp as ufw log

Oct 14 23:56:05 media2 kernel: [26278.785304] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:6e62:6dff:fee0:df01 DST=fe80:0000:0000:0000:1240:f3ff:fe7b:3a84 LEN=78 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=6881 DPT=6$
O

---

