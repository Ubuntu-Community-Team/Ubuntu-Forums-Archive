---
title: "No user has admin privilages"
date: 2006-12-20
forum: General Help
---

### Post by anilat3r on 2006-12-20
I'll make it short and simple

I have 3 active users on a family PC with Ubuntu installed. None have the ability to do administrative functions, nothing beyond the basic user functions which include:device manager, network tools, system log, printing and system monitor. 

I have enabled and logged in as root, and even the root account has no administrative abilities. 

Anybody have any ideas?

I was thinking about trying to reassign user rights to my account through the terminal but I don't know how or if you even can. 

If it is important how I got myself into this mess I can explain, however I wanted to keep this post short.

Thanks

---

### Post by wireddad on 2006-12-20
I have had that issue.  Restarted and the root password worked again.  Can you do anything as root?

---

### Post by riven0 on 2006-12-20
If nothing else works, boot up into recovery mode and do:

> addgroup **yourusername** admin

That worked for me when my sudo privileges got messed up.

---

### Post by aysiu on 2006-12-20
> **riven0 said:**
> If nothing else works, boot up into recovery mode and do:



That worked for me when my sudo privileges got messed up.
Step-by-step instructions are here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

