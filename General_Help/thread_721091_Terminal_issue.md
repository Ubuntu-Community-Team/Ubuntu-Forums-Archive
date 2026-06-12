---
title: "Terminal issue"
date: 2008-03-11
forum: General Help
---

### Post by mikedoth on 2008-03-11
I've been logging into my xubuntu server using putty/ssh just fine. I've recently run into an issue when I want to connect from that server to another xubuntu system.

Windoz(putty) -> Xubuntu(node000-server) -> Xubuntu(node001)

When i'm logged into node000 I can issue commands to my hearts desire, but then rsh'ing into node001 it appears like i'm re-logging into the node000 and my prompt stays the same ###@node000$. Doing a who command says i'm connected on pts/0 to node001 but I have no idea how to access it to actually use the system. Please help!

Mike

---

### Post by dokdoom on 2008-03-11
Did you build these servers? Do they have IPTables blocking any connections? Also are you really using RSH? Is there a reason you aren't just SSH'ing?

---

### Post by mikedoth on 2008-03-11
Is there a way to jump in and out of the connection to node001 while inside my putty connection to node000?

---

