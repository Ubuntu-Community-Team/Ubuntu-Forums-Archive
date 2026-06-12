---
title: "Firstarted stoped working after upgrade to Feisty"
date: 2007-04-30
forum: General Help
---

### Post by johanPO on 2007-04-30
I did an upgrade. Apart from having other issues, I now notices that firestarter is not working

gksudo firestarter

generates an error /var/log/Xorg.0.log
AUDIT: Mon Apr 30 20:52:10 2007: 5340 X: client 37 rejected from local host (uid 0)

Anyone has ideas about this?

---

### Post by Oki on 2007-04-30
Firestater is just an frontend for the firewall within Ubuntu(ip tables?), so I don’t think your firewall is not working. Try to reinstall firestater after removing it.

But no, I dont know more.

---

### Post by johanPO on 2007-05-01
Nop that does not work. 

after a complete removal and installation I still get 
AUDIT: Tue May  1 10:25:52 2007: 5179 X: client 36 rejected from local host (uid 0)

also I doubt that iptables is running

johan@johans:~$ ps -aux | grep ip
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
hplip     5240  0.0  0.4   9988  4892 ?        S    09:56   0:00 python /usr/sbin/hpssd
johan    14882  0.0  0.0   2888   772 pts/0    S+   10:50   0:00 grep ip

contemplating to make a fresh install of Feisty, or downgrade....

---

