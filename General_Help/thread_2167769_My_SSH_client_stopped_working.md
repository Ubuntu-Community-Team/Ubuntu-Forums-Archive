---
title: "My SSH client stopped working"
date: 2013-08-14
forum: General Help
---

### Post by PR4rHyf on 2013-08-14
I am running Ubuntu 13.04 and my SSH client suddenly stopped working.  Actually, I don't think it is my client at all since I can launch a Windows VM via VMware Workstation and it cannot SSH to anything either.  I can SSH from the same network using my phone, however.  This makes me think that something is blocking port 22 but I have stopped UFW and I still have the issue.  I can't think of anything that has changed.  Any ideas?

Justin

---

### Post by Habitual on 2013-08-19
```
ssh -v user@host
``` output (sanitized of course) please.

---

### Post by PR4rHyf on 2013-08-19
It turned out to be a network firewall issue.  It was odd that the firewall was only denying my 1 IP.  I don't have any specific IP's in the rules.  Thanks for your help though!

---

### Post by Habitual on 2013-08-19
Glad it worked out!

---

