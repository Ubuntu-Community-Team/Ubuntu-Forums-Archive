---
title: "Error shortly after an  update."
date: 2014-02-15
forum: General Help
---

### Post by Silvernail on 2014-02-15
I've been getting this error for a couple of days. What is causing it and what do I  need to do to eliminate it?

> dave@Dafydd:~$ sudo youtube-dl -U
sudo: unable to resolve host Dafydd
[sudo] password for dave: 

And then all seems to work.

---

### Post by fdrake on 2014-02-15
what is the output of ```
cat /etc/hostname
```

---

### Post by Silvernail on 2014-02-16
dave@Dafydd:~$ cat /etc/hostname
Dafydd
dave@Dafydd:~$ 
-rw-r--r-- 1 root root 7 Feb 15 01:56 hostname
Should it be somewhere else? 

> dave@Dafydd:/etc$ sudo grep -Ri 'Dafydd' *
sudo: unable to resolve host Dafydd
[sudo] password for dave: 
Binary file aliases.db matches
cups/printers.conf.O:Location Dafydd
cups/printers.conf:Location Dafydd
hostname:Dafydd
postfix/main.cf:myhostname = Dafydd
postfix/main.cf:mydestination = embarqmail.com, Dafydd, localhost.localdomain, localhost
printcap:ML-2010|Samsung ML-2010:rm=Dafydd:rp=ML-2010:
dave@Dafydd:/etc$ 


---

### Post by fdrake on 2014-02-16
any chance that your hostname is missplelled in /etc/hosts ? post your "cat /etc/hosts "
did you play with the domanin name somewhere in your net settings?

---

