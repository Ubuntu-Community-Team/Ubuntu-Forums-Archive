---
title: "Clarification on the differences between sudo and gksudo"
date: 2006-11-07
forum: General Help
---

### Post by Zunino on 2006-11-07
Hello.

I had once been told that *gksudo* should be used when wishing to launch graphical applications as 'root', just as *sudo* does for text-based ones. However, everytime I use *gksudo*, I get a message like the following:
```
(gedit:6442): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```
On the other hand, if I use *sudo,* everything works (apparently) and no error message is produced.

I would like to understand the **actual** differences between the two alternatives. What are the implications of using *sudo* instead of *gksudo* to launch graphical applications, if any? When must one use *gksudo*?

Thank you,

-- 
Ney André de Mello Zunino

---

### Post by BitTorrentBuddha on 2006-11-07
One never actually has to use gksudo (which I believe is depreciated by gksu) but it makes launching applications as root much easier if you're doing it from a menu.

---

### Post by taurus on 2006-11-07
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dcstar on 2006-11-08
> **taurus said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

You know, when I read a page like that which explains an issue for the benefit of those of us that need this sort of info, I am reminded of the great thing that the Internet can be for someone to go to the trouble to do this for the benefit of others.

Well done, that person!!!!              :p

---

