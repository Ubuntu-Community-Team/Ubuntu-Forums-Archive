---
title: "Is there a way to track data transfer activity?"
date: 2007-04-03
forum: General Help
---

### Post by timka1 on 2007-04-03
I am running Dapper Ubuntu on an old AMD 1GHz machine and it's been generally smooth and brought a new lease of life to the old box.

However yesterday I got an alert from my ISP that I had exceeded my data traffic allowance and the data usage showed over 700MB for the day. Since my other machines were sleeping I guess it was the Ubuntu machine.

My question is: is there a log file somewhere in Ubuntu that shows what data traffic there has been?

I am also wondering whether there has been an automatic upgrade which caused this spike. If so can I set it to take place after midnight when data traffic is free?

Could I have a virus?

Thanks in advance.

---

### Post by nsleiman on 2007-04-03
The probability of being infected with a virus on a linux box is very low i guess,

maybe its the updater ? (adept_updater maybe?)

i remember first time i installed Kubuntu i updated the system with 196MB :) 

as for the log files take a look in:
/var/log

(look for messages, lastlog, wtmp...)

thats what i know :)

---

### Post by teaker1s on 2007-04-03
I'd be interested in this too, I'm running 8mbit/s and unlimited connection-but I'd still like to fully know how much I'm using

---

### Post by fanatik on 2007-04-03
Well you could use iptables to monitor it, I've done this in the past. Iptables can show you how many bytes have been received since the box was last rebooted/or the stats zeroed. I can't remember if you need to enable anything to get this to work, but here's my output of the relevant bit:

```
[FONT="Courier New"]james@maple:~$ sudo iptables -vnL |grep eth
 820K  459M eth0_in    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0   
    0     0 eth0_fwd   all  --  eth0   *       0.0.0.0/0            0.0.0.0/0   
   21  7015 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
 398K   83M fw2net     all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           policy match dir out pol none[/FONT]

```

This is showing that I have received 459M and sent 83M in the last 7 days since my pc has been running.

It won't show what is using this, just the amount of data flowing through your interface.

Regards,
James.

---

