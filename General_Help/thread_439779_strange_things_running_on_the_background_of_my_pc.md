---
title: "strange things running on the background of my pc"
date: 2007-05-11
forum: General Help
---

### Post by odysseus.lost on 2007-05-11
Hi,

not being paranoid but recently I discovered that there are some things that are running short while after I logon to my system, perl scripts, sed, gzip, all as root and then they stop. I am not sure if they are running always.... Is this normal? Is there any way I could investigate what are these things that are running and what they do?

Thanks.

---

### Post by seshomaru samma on 2007-05-11
what is the name of these 'things'?
how did you discover they are running on your machine?
the command 
```
ps aux
```
will tell you whats running on your machine

---

### Post by kerry_s on 2007-05-11
sounds like the update manager.

---

### Post by odysseus.lost on 2007-05-11
thanks for the help... i discovered them when my fan was going crazy indicating some heavy usage of my cpu.... i showed them using top.... but can't post anything else now as they "only seem" to logon upon logon... i was wondering if there any particular log i could have a look...

---

### Post by fakie_flip on 2007-05-11
Do you think someone may be hacking into your system or installed a rootkit? Install chkrootkit and run it.

---

### Post by odysseus.lost on 2007-05-11
> **fakie_flip said:**
> Do you think someone may be hacking into your system or installed a rootkit? Install chkrootkit and run it.

Thanks. I ll have a look at it.

---

