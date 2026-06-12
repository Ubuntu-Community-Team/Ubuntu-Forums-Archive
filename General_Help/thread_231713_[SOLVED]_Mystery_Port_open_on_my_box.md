---
title: "[SOLVED] Mystery Port open on my box"
date: 2006-08-07
forum: General Help
---

### Post by vayde on 2006-08-07
Anyone know what might be using port 1019?  For some reason it's open, and listed as 'unknown'.  This bothers me somewhat.  I can't think as to what might be using it.

EDIT: Nevermind.  Had to run netstat -anp as root and rpc.statd turned out to be the culprit.  NFS thing apparently.  

Isn't if funny that the answer comes right *after* I post a thread?

---

### Post by CameronCalver on 2006-08-08
Yes that has happened to me before then you feel like a spammer because you ask a question then say don worry fixed lol

---

