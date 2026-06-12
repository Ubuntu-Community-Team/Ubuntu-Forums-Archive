---
title: "Deja Dup resolves host name incorrectly"
date: 2013-03-05
forum: General Help
---

### Post by shakabra on 2013-03-05
**PROBLEM:**
I backup to an SSH server via Deja Dup. Recently I am recieving warnings that: my backups are for a computer called 'my_actual_hostname' but the current computer is 'my_hostname.hawaii.rr.com'.

My questions are:
How is Deja Dup resolving my hostname? I have my hostname in /etc/hostname. Python resolves the correct hostname with socket.getfqdn().

Where should I look to troubleshoot? I have already reset my router to factory default.

What could cause Deja Dup, or duplicity, to tack on my ISPs name to my computer name?

---

### Post by dcstar on 2013-03-07
> **shakabra said:**
> **PROBLEM:**
I backup to an SSH server via Deja Dup. Recently I am recieving warnings that: my backups are for a computer called 'my_actual_hostname' but the current computer is 'my_hostname.hawaii.rr.com'.

My questions are:
How is Deja Dup resolving my hostname? I have my hostname in /etc/hostname. Python resolves the correct hostname with socket.getfqdn().

Where should I look to troubleshoot? I have already reset my router to factory default.

What could cause Deja Dup, or duplicity, to tack on my ISPs name to my computer name?

```
cat /etc/hosts
cat /etc/resolv.conf
```

---

### Post by shakabra on 2013-03-07
David, I was just about to reply with a snarky post about how reading out a file would not help. But then it dawned on me. When I installed this system I initially had a weird username so I changed it in /etc/hostname. I forgot to change it in /etc/hosts. 

Aloha

---

