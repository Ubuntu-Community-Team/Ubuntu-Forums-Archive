---
title: "iptables blocked ip - see attempts to connect"
date: 2016-04-03
forum: General Help
---

### Post by marchello_lippi2 on 2016-04-03
Hi all, 

I got some iptables rules to block incoming connections from different ip, how do I see attempts to connect? 
Thanks ahead.

---

### Post by SeijiSensei on 2016-04-03
Add a rule identical to the blocking one and place it above the blocking rule.  Use the target "-j LOG" instead of "-j REJECT".  Now an entry will be written to /var/log/syslog for every matching event; the blocking will still take place.

---

### Post by marchello_lippi2 on 2016-04-04
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"), 

Could you please also tell me how should mentioned event look like in /var/log/syslog ?

---

### Post by SeijiSensei on 2016-04-05
Something like this:
```
Apr  5 16:58:09 mail kernel: IN=eth0 OUT= MAC=f2:3c:91:6e:d1:36:84:78:ac:0d:79:c1:08:00 SRC=183.60.208.176 DST=50.X.X.X LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=31360 DF PROTO=TCP SPT=51426 DPT=XXXX WINDOW=8192 RES=0x00 SYN URGP=0
``` 

Try "grep kernel /var/log/syslog".  All the iptables logging is handled by the kernel.

---

### Post by marchello_lippi2 on 2016-04-13
Tried 

sudo grep kernel /var/log/syslog

and 

sudo grep -i "kernel" /var/log/syslog

no results. 

In fact, I can see that those who tried to connect to my main mx server now try to connect via my secondary backup mx server. So it does work to block. It does not work to log or I do not have enough knowledge to see it. 
Any other suggestions how to see attemts to connect? 
Thanks ahead.

---

### Post by SeijiSensei on 2016-04-13
Post your iptables ruleset inside of [noparse]```

```[/noparse] tags.

However it sounds like these attempts are made against a mail server.  You should see every connection in /var/log/mail.log if you remove the iptables rules.  If you're trying to identify annoying servers, I'd just scan that log every now and then to see which IPs are trying to connect.  I'll warn you though that trying to control mail via sender's IP is not an easy task.  There are way too many machines sending spam and malware to block them by IP address.  You'll be in a constant game of cat-and-mouse.  If you're running Postfix, you need to write some rules like those described in [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html).  Pay special attention to directives like smtpd_helo_restrictions, smtpd_sender_restrictions, and similar restrictions for starters.

---

