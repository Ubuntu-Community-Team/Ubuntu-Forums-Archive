---
title: "Help diagnosing postfix issue"
date: 2007-11-22
forum: General Help
---

### Post by ryankask on 2007-11-22
I am getting the following error from some hosts:

Nov 22 09:56:40 ubuntu postfix/smtp[24748]: 7E1D223523: to=<sk8artomo@mail386.com>, relay=mxa.mail386.com[216.17.109.154], delay=54075, status=deferred (host mxa.mail386.com[216.17.109.154] said: 450 <info@languaglab.com>: Sender address rejected: Domain not found (in reply to RCPT TO command))

What does this mean and how can I fix it?

---

### Post by mannih2001 on 2007-11-22
It means that your postfix server was trying to pass on a message from [email]info@languaglab.com[/email], but the server that acts as a relay told it that it doesn't want to deal with that message since it doesn't know about the domain languaglab.com. 

You can fix it by entering a correct From-address in your email client.

---

### Post by ryankask on 2007-11-22
Hmm...languagelab.com is a valid domain though. 

; <<>> DiG 9.3.2 <<>> languagelab.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53450
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;languagelab.com.               IN      A

;; ANSWER SECTION:
languagelab.com.        600     IN      A       88.208.206.14

;; Query time: 126 msec
;; SERVER: 213.171.192.249#53(213.171.192.249)
;; WHEN: Thu Nov 22 16:45:16 2007
;; MSG SIZE  rcvd: 49

Is it because the host's name is ubuntu and ubuntu.languagelab.com isn't a valid domain?

---

### Post by mannih2001 on 2007-11-22
Yes, languagelab.com is a valid domain name.
But languaglab.com isn't. Note the missing 'e'.

---

### Post by ryankask on 2007-11-22
haha thank you!!

---

