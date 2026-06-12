---
title: "Can't use secure connection in Mail Notification"
date: 2005-10-15
forum: General Help
---

### Post by niels on 2005-10-15
I have tryed to set-up Email Notification to tjek my IMAP mailbox. The problem is, that i wasn't able to choose the secure connection types ('in-band SSL/TLS' og 'SSL/TLS on separate port'). If I can't use these options, the notifier is useless... Please help!

Niels

---

### Post by ember on 2005-10-16
I don't have a solution, yet the same problem. OpenSSL and Cyrus SASL library are installed. So I wonder what is missing.

---

### Post by plutoprime on 2005-10-16
SSL support is not compiled in due to Retarded licence problems from debian that found it's way to ubuntu. I made a package for my personal use using "checkinstall" for version 2.0 and it works great.

---

### Post by lewiz on 2005-10-16
Any chance you could provide a link to your deb?  :P

---

### Post by niels on 2005-10-17
[QUOTE=plutoprime]SSL support is not compiled in due to Retarded licence problems from debian that found it's way to ubuntu. I made a package for my personal use using "checkinstall" for version 2.0 and it works great.[/QUOTE]
How did you do this - would be nice with a .deb if possible.

---

