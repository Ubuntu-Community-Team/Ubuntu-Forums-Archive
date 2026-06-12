---
title: "ddclient and ssh"
date: 2021-01-28
forum: General Help
---

### Post by miniu2 on 2021-01-28
[FONT=arial]Hi
[/FONT]
[FONT=arial]I would like to connect remote to my ubuntu via ssh.
[/FONT]
[FONT=arial]To complite this task i created account on dynu.com[/FONT]
[FONT=arial]I instaled ddclient and configure like:
[/FONT]

 
 ```
[I]# /etc/ddclient.conf
daemon=60                           
syslog=yes                          
use=web, if=eth0
server=api.dynu.com
protocol=dyndns2                        
login=zapka                         
password="#Chomik22"              
zabka.mywire.org[/I]
``` T[FONT=arial]he command:[/FONT]

 
 
```
*# sudo ddclient -daemon=0 -debug -verbose -noquiet*
``` 
Returns this

```
SUCCESS:  zabka.mywire.org: skipped: IP address was already set to "99.221.135.14".
``` But:
```
*# ssh zabka@zabka.mywire.org *
```
Finish with timeout

 
 Is my point of view correctly? Or maybeon my router port 22 is blocked?

---

### Post by TheFu on 2021-01-28
DNS can take some time for an update to propagate. 5 minutes  - 7 days are common settings.

I scanned the IP 99.221.135.14 - no inbound ports were listening.  
If that is the correct IP, either the ISP blocks all inbound conections
or
something else is blocking inbound connections (LAN router or SW firewall)
or
the listener isn't running.

Lastly, please ensre the password inyor ddconf file is NOT correct. These are quite public forums.

---

### Post by TheFu on 2021-01-28
```
$ dig zabka.mywire.org
```

doesn't return the correct answer.

---

### Post by miniu2 on 2021-01-29
Thanks for your time and a warning but, I changed intentionally this data like IP, login, password. I know this site is public.

```

micha@sss:~$ dig zabka.mywire.org

; <<>> DiG 9.16.1-Ubuntu <<>> xxx.mywire.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21453
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;zabka.mywire.org.        IN    A
;; ANSWER SECTION:
xxxx.mywire.org.    299    IN    A    xx.xx.xx.xx

;; Query time: 451 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: pi&#261; sty 29 08:45:53 CET 2021
;; MSG SIZE  rcvd: 61
```

I did what you say, and you see the outcome, and do you have an idea what is wrong?

---

### Post by TheFu on 2021-01-29
Well, if you don't post actual public information, it is hard to help.  Would have been nice if you'd said that above. Good luck.

From here, dig zabka.mywire.org doesn't return any valid A records.

```
$ dig zabka.mywire.org

; <<>> DiG 9.16.1-Ubuntu <<>> zabka.mywire.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 48814
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;zabka.mywire.org.              IN      A

;; AUTHORITY SECTION:
mywire.org.             1800    IN      SOA     ns1.dynu.com. administrator.dynu.com. 5076837 1800 300 86400 1800

;; Query time: 76 msec
```

---

### Post by miniu2 on 2021-01-29
Here you have correct data ... 
```
# dig miniu.mywire.org
```

Thanks for your time

---

### Post by ActionParsnip on 2021-01-29
I get 91.225.185.142 for that hostname

---

### Post by miniu2 on 2021-01-30
It it possible to get a remote  connection to an ssh client that has a non-static ip (for free)  ?

---

