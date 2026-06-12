---
title: "linuxptp: phc2sys doesn't sync the system clock"
date: 2017-12-15
forum: General Help
---

### Post by opighi on 2017-12-15
Dear all,
I have ubuntu 16.04 installed on two different PC , and another embedded "ARM" based system.
i have installed linuxptp 1.8 on all of them. (i'm using HW sync ptp so i configured ptp and phc as well)
the ARM system acts as master (it is connected to a gps recevier) , to obtain that it is always the Grand master i have configured its config file with a low priority1 (100). 
this make it always the grand master of my network.
the system worked for several week without any problem.
i used to check the sync status with 
tail -f /var/log/syslog | grep ptp
tail -f /var/log/syslog | grep phc

the output is something similar to

Dec 14 16:08:34 it-eva-driving phc2sys: [23058.294] phc offset 10512340976 s2 freq +100000000 delay   2892

and i can see the offset decreasing until reach the sync and then stay almost stable under 1 msec of delta from the master on both ptp and phc control loop.

but one day the phc stopped to work , on both PC 
I mean:
tail -f /var/log/syslog | grep ptp
show , as usual, the offset decreasing and the stay stable this mean the ethernet board are in sync.

but with
tail -f /var/log/syslog | grep phc 

Dec 14 16:08:34 it-eva-driving phc2sys: [23058.294] phc offset 10512340976 s2 freq +100000000 delay   2892
the offset diverge and always increase..

any idea?
thankyou
Omar

---

