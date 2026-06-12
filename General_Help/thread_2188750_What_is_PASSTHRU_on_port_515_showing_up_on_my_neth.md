---
title: "What is PASSTHRU on port 515 showing up on my nethogs?"
date: 2013-11-18
forum: General Help
---

### Post by azhar.basit on 2013-11-18
HI,  First time I am posting here.  Attaching the screen capture of my nethogs output , hope it uploads.  What is this /PASSTHRU on port 515 intermittently showing up on my nethogs.  I could not find it in google :o

---

### Post by sammiev on 2013-11-18
Usually for a wireless printer.

---

### Post by azhar.basit on 2013-11-19
thank you!

---

### Post by efflandt on 2013-11-19
Port 515 has been used for lpr/lpd type printing since before cups, supported by most all print servers, and still used. /etc/services is a list of ports typically associated with services. Keep that in mind when trying to figure out what a port is for:
```
efflandt@xps8100-1204:~$ grep 515 /etc/services
printer        515/tcp        spooler        # line printer spooler
pcrd        5151/tcp            # PCR-1000 Daemon
```

---

