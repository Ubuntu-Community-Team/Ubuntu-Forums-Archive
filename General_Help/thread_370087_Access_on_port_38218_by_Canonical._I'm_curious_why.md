---
title: "Access on port 38218 by Canonical. I'm curious why?"
date: 2007-02-25
forum: General Help
---

### Post by tebibyte on 2007-02-25
Hello all. I was just checking my firewall logs. I use fire starter. I came across some blocked packets from ip address 91.189.89.8 and 91.189.89.6. they were trying to access ports 38218, 31896, 60901, and 54204. I whois'd them, and the whois server said that the Ip address was registered under Canonical.  I'm curious as to what the packets where intended to do. It's not a big deal. Thanks.

---

### Post by clooch on 2007-02-25
i found the same thing, I can not update without it hiting fire starter and giving me the same message. how ever I can't for the life of me allow any of these  through so I can update my system. :( 

if any one has any ideas it would be welcome. 

thank you

---

### Post by tebibyte on 2007-02-25
Oh...that must be what it is doing. I'm having the same problem. I'm going to turn firestarter off, and see if it will update.

 You can turn off firestarter  by going to system-> administration->firestarter.

Type in the administrative password and hit the stop firewall button

You can also allow the updates while leaving the firewall on by right clicking the event log and hit allow connections from source.

It looks like we killed two birds with one stone.

---

