---
title: "Mail Server Setup"
date: 2013-06-10
forum: General Help
---

### Post by DDDEMON on 2013-06-10
Anyone got a good tutorial on how to setup a mail server I have tried most that I could find on the internet with a :( result. 
Was going for postfix/devcote, or courier, MySQL pop3/imap/ssl/tls setup. I have almost won but reformatted since I could not get the smtp to send mail from outlook on Microsoft. 1 week of trying mult tutorials and failing. Started to look at microsoft lol but no I will not surrender to that price tag..... Anyone got a walk through that I can win with thanks

---

### Post by HermanAB on 2013-06-11
Right from the horse's mouth: [http://www.postfix.org](http://www.postfix.org)

---

### Post by lisati on 2013-06-11
A links with Ubuntu connections:  [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
There are plenty of others to be found on [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by JKyleOKC on 2013-06-11
> **lisati said:**
> A links with Ubuntu connections:  [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
There are plenty of others to be found on [https://help.ubuntu.com/](https://help.ubuntu.com/)The Postfix link says it was tested " on Ubuntu 6.06 (Dapper) and Ubuntu 7.10 (Gutsy)." Is it still applicable with no change now that the current LTS is 12.04?

---

### Post by sandyd on 2013-06-11
If you just want a 'just works' solution, you might want to try Zimbra, Axigen, or iRedMail. IredMail is a *bit* complicated to upgrade whenever there are updates, but is essentially postfix+amavis+spamassassin with a web interface (iredadmin)

---

