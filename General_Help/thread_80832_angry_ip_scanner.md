---
title: "angry ip scanner"
date: 2005-10-23
forum: General Help
---

### Post by stoeptegel on 2005-10-23
I am looking for a similar tool for linux, does someone know one maybe?

---

### Post by heimo on 2005-10-23
I don't know this particular scanner, but how about [nmap]("http://packages.ubuntu.com/breezy/net/nmap")? In universe, there's front end for it (haven't used this), [nmapfe]("http://packages.ubuntu.com/breezy/net/nmapfe").

EDIT: Oh! I don't often recommend reading man pages (even though I think those are extremely useful), but you really don't want to miss nmap's man page. Also here's the [homepage]("http://www.insecure.org/nmap/").

---

### Post by tonysathre on 2005-10-24
netcat (nc) is a very useful tool

angry ip scanner is a windows program and isnt very good, if you want a better one get foundstone's SuperScan

---

### Post by stoeptegel on 2005-10-28
Thanks netcat did the job. :-)

---

### Post by gdw2 on 2007-12-05
I would also suggest nmap....

(sudo apt-get install nmap)

this scans 192.168.1.0 - 192.168.1.256...

nmap -v -sP 192.168.1.0/24

---

