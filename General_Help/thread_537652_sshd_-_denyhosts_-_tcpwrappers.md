---
title: "sshd - denyhosts - tcpwrappers"
date: 2007-08-29
forum: General Help
---

### Post by posterboy on 2007-08-29
OK, I googled, read the threads here, read the man pages, there's a tutorial here, I followed. None of this worked for me. I run sshd, and denyhosts. I set up the denyhosts.conf to suit. I set it for 3 attempts. That's ignored. After 5 attempts, it fails, but nothing is written into /etc/hosts.deny. Useless. Clues: Ignores my 3 attempts setting. ANY IP I put in hosts.deny, is being ignored. The form I am using is ALL: XX.XX.XX.XX. Also tried GDM:XX.XX.XX.XX as suggested someplace. Hosts.deny is set 600, but I also tried 666. Now, out of ideas. HELP!
TIA, Ray

---

### Post by posterboy on 2007-08-29
Never mind, I got it working. I don't like to leave a thread like this, but I honestly do not know what fixed it. Making lots of changes, sometimes does that to me. :)

---

### Post by 3rods on 2007-09-06
posterboy, 

Check out OSSEC (OSSEC.net). It does the same things as denyhosts, but it also adds them to iptables plus it does a whole lot more; and it's easier to setup. 

I was running denyhosts until I read about the possibilities for exploiting denyhosts (DoS, etc) and then I switched to OSSEC. It's realy good it does log analysis, integrity checking, rootkit detection, real-time alerting and active response. And it will email you if new users log in or sudo that it hasn't seen before. 

Not only will it add the host to hosts.deny, but it will create an iptables rule as well, which I hear, is the better way to do it.

It's pretty neat. I'm impressed.

---

### Post by posterboy on 2007-09-07
Thank you, on the way to see about it.

---

