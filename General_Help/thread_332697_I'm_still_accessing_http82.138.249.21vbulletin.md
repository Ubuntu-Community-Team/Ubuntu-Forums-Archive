---
title: "I'm still accessing http://82.138.249.21/vbulletin"
date: 2007-01-06
forum: General Help
---

### Post by chrispche on 2007-01-06
As opposed to [www.urban75.net/vbulletin](www.urban75.net/vbulletin). It worked for awhile for a few days ago and then I'm back to the using the IP address. Anyone have any ideas? This all happened when I changed to Ubuntu. Although that could be coincedence bareing in mind my location is South Africa.

---

### Post by koenn on 2007-01-06
what do you get from
```
dig www.urban75.com
```
& let's have a look at your /etc/resolv.conf

---

### Post by chrispche on 2007-01-07
It's [www.urban75.net](www.urban75.net) forget .com I can get that. Let me see...

---

### Post by chrispche on 2007-01-07
Ok I get:

chrispche@chrispche-desktop:~$ dig [www.urban75.net](www.urban75.net)

; <<>> DiG 9.3.2 <<>> [www.urban75.net](www.urban75.net)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57148
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.urban75.net](www.urban75.net).               IN      A

;; ANSWER SECTION:
[www.urban75.net](www.urban75.net).        86400   IN      A       82.138.249.21

;; Query time: 298 msec
;; SERVER: 168.210.2.2#53(168.210.2.2)
;; WHEN: Sun Jan  7 09:56:49 2007
;; MSG SIZE  rcvd: 49

chrispche@chrispche-desktop:~

Let me find that file you want to take a look at and I'll post it.

---

### Post by chrispche on 2007-01-07
Ok it's just standard DNS's

nameserver 168.210.2.2
nameserver 196.14.239.2

---

### Post by koenn on 2007-01-07
looks OK to me - your DNS server returns the same address as the one you're using in the firefox address bar, so there's no reason that the url shouldn't work also. 
except maybe : are you using a www proxy (either your own, your ISP's, ...) ?

---

### Post by chrispche on 2007-01-08
No I'm not. This is highly strange. I even called the ISP and they can resolve it fine there end.

---

