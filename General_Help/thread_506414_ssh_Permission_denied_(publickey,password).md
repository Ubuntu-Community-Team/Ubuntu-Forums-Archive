---
title: "ssh Permission denied (publickey,password)"
date: 2007-07-21
forum: General Help
---

### Post by dudous on 2007-07-21
Hi folks,
i'm trying to set up a ssh server on my ubuntu box but i'm having problem with password authentication.
I've installed openssh-server package and using the default /etc/ssh/sshd_config file i can log in locally but from the outside (internet) i got a 
"Permission denied (publickey,password)." error !

for example : 

ssh username@localhost  
shh username@192.168.1.3 (machine's fixed IP)

is  OK   but :

ssh username@INTERNET_ADDRESS or ssh username@INTERNET_DOMAIN

gives me the error.

I've tried both with root and normal users.
It seems like my router is port forwarding port 22 to 192.168.1.3 correctly since i can stablish a conection except the authentication. Iptables is with no rules.

it's like the ssh server is rejecting all that's not from 192.168.1.0 network.

I've been searching the web for this issue and found nothing so far.

Please, does anybody knows what can be wrong ?

Thanks in advance

---

### Post by HermanAB on 2007-07-21
Try dig or nslookup to confirm that the DNS is OK.

---

### Post by dudous on 2007-07-21
Both commands seems to be alright.

Responses bellow (addresses modified for security) :

nslookup  domainname
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   domainname
Address: my_internet_address

dig domainname

; <<>> DiG 9.3.4 <<>> domainname
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57373
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
domainname.          IN      A

;; ANSWER SECTION:
domanname.   60      IN      A       my_internet_address

;; Query time: 265 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Jul 21 18:20:35 2007
;; MSG SIZE  rcvd: 54

---

### Post by Mr. C. on 2007-07-21
Increase LogLevel in your sshd_config file, or stop the sshd server and start it in a shell with the -d option.  Examine the auth.log to see where the authentication is failing.  LogLevel is described in man sshd_config , and the -d option is in man sshd.

MrC

---

### Post by dudous on 2007-07-21
ok. I put LogLevel to DEBUG3 , restarted sshd and tried to login again.

doing a "cat /var/log/auth.log" gave me this lines from the sshd server :

Jul 21 19:36:19 dudous sshd[8792]: Received signal 15; terminating.
Jul 21 19:36:19 dudous sshd[15132]: debug2: fd 3 setting O_NONBLOCK
Jul 21 19:36:19 dudous sshd[15132]: debug1: Bind to port 22 on 0.0.0.0.
Jul 21 19:36:19 dudous sshd[15132]: Server listening on 0.0.0.0 port 22.

i think the first line and so on, was generated after my three attempts to insert my password. For some reason it not recognizes my password when i connect from the outside. odd !

---

### Post by Mr. C. on 2007-07-21
If those are the only lines *and* you are attempting to connect, then the SSH server is not receiving your connection.  Connect from the server itself, and compare the output.

MrC

---

### Post by dudous on 2007-07-21
You are soo right Mr. C.
My router is not forwarding port 22. it has his own ssh server and i'm not having success disabling it.  It seems this router has some bugs (dsl-g624t)
Now i'm trying to use a different port to make the port forwarding.
But it's ok. At least know i know what i should do.
I think i can do it by myself now.

Thanks to everybody. 
Helped a lot !

---

### Post by dudous on 2007-07-24
Solved !

I realized that this router doesn't do NAT LOOPBACK. That is, it doesn't accept connections from my internet address to my inside my lan, originated from the lan.

So, from inside i make connections with local addresses and people who are outside can make the connections without problems. 

I don't know why it is that way, but i was told that this is to prevent a security flaw... 

bye

---

### Post by Mr. C. on 2007-07-24
Now, see, this is where showing output, instead of interpreting output is so critical.  You had said:

> ...but from the outside (internet) i got a "Permission denied (publickey,password)." error !

You were not on "the outside", you were on the inside!  An couple of commands would have cleared that up, and I would have mentioned that NAT loopback is unsupported in many routers.

Oh well, next time...
MrC

---

