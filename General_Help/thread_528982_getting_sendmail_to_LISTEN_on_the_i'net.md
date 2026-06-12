---
title: "getting sendmail to LISTEN on the i'net"
date: 2007-08-18
forum: General Help
---

### Post by posterboy on 2007-08-18
OK, this my SECOND day with Ubuntu. I REALLY don't know what I'm doing. I come here from FC6.
I _think_ I have sendmail configured workably, maybe, as it will handle mail just fine on the local box, but, look at this nmap run on my i'net IP:
PORT     STATE  SERVICE
22/tcp   closed ssh
25/tcp   closed smtp
113/tcp  closed auth
4662/tcp closed edonkey

Huh? I have a hardware firewall, but I am certain 25 is open there, and sendmail works fine on FC6. What is it I don't know? 

Another thing. Spamassassin is missing several perl modules. I have had bad luck with CPAN in the past, is there a repo where I can find those? 

TIA, Ray

---

