---
title: "Logging NAT Transactions"
date: 2014-01-10
forum: General Help
---

### Post by netmonky on 2014-01-10
Hi Guys,

Quite new to linux and have been playing quite heavily with iptables/conntrackfor the past few weeks. I have searched high and low for this answer and am sure it can be done -somehow. Basically, I masquerade quite a lot of connections but I now need to be able to track who had what IP/Src port at what time by logging the NEW and TEARDOWN NAT translations. Is this possible?

---

### Post by SeijiSensei on 2014-01-10
Just write a rule with syntax identical to the rule you want to log and put the new rule above the old one.

For instance, I usually have a catch-all rule at the bottom of the iptables ruleset to deny all unmatched traffic.  I'll usually include a logging rule just above it like this:

```

/sbin/iptables -A INPUT -j LOG
/sbin/iptables -A INPUT -j REJECT

```

You can use the [--log-prefix option]("http://linux.die.net/man/8/iptables") to tag packets that match a particular rule.

---

### Post by netmonky on 2014-01-12
Yes but if I am natting i want something like  srcIP srcPort destIP destPort NatAddress NatSrcPort. Something similar to conntrack -E output maybe but logging to a file. I can do this with Cisco ACE's (on large scale nat) - was wondering if it could be done on linux as well :-). Unsure if you can match against transaction status events - ie: teardown

---

### Post by Doug S on 2014-01-12
There may be an easier way, but what I do is two tcpdump sessions always running on my system saving the data as files, one on the LAN side and one of the WAN side. The tcpdump files are in 10 minute chunks, auto changing. Then, if I need to trace back something, I figure it out as a post process.

For example, I got an e-mail from my ISP one time saying that I had been a bad boy. Given the time range of the issue, I was easily able to isolate the issue down to my nephews computer, when it was on my LAN one time so he could print a homework assignment.

---

