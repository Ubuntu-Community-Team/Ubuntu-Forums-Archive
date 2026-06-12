---
title: "IPtables UTC time  issue in Ubuntu 16.04"
date: 2018-06-15
forum: General Help
---

### Post by deepanstack on 2018-06-15
Hi Team,
Im trying to run IP tables command due to UTC time sync issue its not getting correctly.
Could you please help me out here, iptables version using is v1.6.0 in ubuntu 16.04

root@cpunode1:/etc# date  à LOCAL TIME
Thu Jun 14 12:27:43 CEST 2018
root@cpunode1:/etc# date -u à UTC TIME
Thu Jun 14 **10:27:46** UTC 2018
root@cpunode1:/etc# sudo iptables -A INPUT -p tcp --destination-port 59402 -j DROP -m time --datestart 2018-06-**14T10:29:38** --datestop 2018-06-**14T10:35:00**   
root@cpunode1:/etc# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
DROP       tcp  --  anywhere             anywhere             tcp dpt:59402 TIME starting from 2018-06-14 09:20:00 until date 2018-06-14 09:30:00 UTC
**DROP       tcp  --  anywhere             anywhere             tcp dpt:59402 TIME starting from 2018-06-14 09:29:38 until date 2018-06-14 09:35:00 UTC**
 
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
 
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@cpunode1:/etc#
 

 Iptables version in ubuntu 16.04
root@cpunode1:/etc# iptables -version
iptables v1.6.0: unknown option "iptables"
Try `iptables -h' or 'iptables --help' for more information.
root@cpunode1:/etc#

Thanks,
Deepan

---

### Post by deepanstack on 2018-06-19
Any reply for this issue ?

---

### Post by Doug S on 2018-06-19
I don't know what to say. It works as expected for me using either iptables version 1.6.0 or 1.6.1.

```
$ sudo iptables -A INPUT -p tcp --destination-port 59402 -j DROP -m time --datestart 2018-06-14T[COLOR="#FF0000"]10:29:38[/COLOR] --datestop 2018-06-14T[COLOR="#FF0000"]10:35:00[/COLOR]
$ iptables --version
iptables v1.6.0
$ sudo iptables -v -x -n -L | grep 59402
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:59402 TIME starting from 2018-06-14 [COLOR="#FF0000"]10:29:38[/COLOR] until date 2018-06-14 [COLOR="#FF0000"]10:35:00[/COLOR] UTC

```

---

