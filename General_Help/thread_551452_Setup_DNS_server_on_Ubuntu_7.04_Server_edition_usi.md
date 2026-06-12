---
title: "Setup DNS server on Ubuntu 7.04 Server edition using Bind 9"
date: 2007-09-15
forum: General Help
---

### Post by breezey on 2007-09-15
I followed the tutorial I found here:

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

to setup dns server on my Ubuntu 7.04 Server edition. But I got ANSWER:0 when I do dig mydomain and can't find mydomain when I do nslookup. Below is the result of both dig and nslookup. I would appreciate if anyone could point me to the problem and how to fix it. Thank you very much.

```
home@ubuntu:/$ dig mydomain

; <<>> DiG 9.3.4 <<>> mydomain
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47194
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mydomain.                      IN      A

;; AUTHORITY SECTION:
mydomain.               38400   IN      SOA     ns1.mydomain. admin.mydomain. 2006081401 28800 3600 604800 38400

;; Query time: 2 msec
;; SERVER: 192.168.1.109#53(192.168.1.109)
;; WHEN: Sun Sep 16 11:23:51 2007
;; MSG SIZE  rcvd: 72

home@ubuntu:/$ nslookup mydomain
Server:         192.168.1.109
Address:        192.168.1.109#53

*** Can't find mydomain: No answer
```

---

