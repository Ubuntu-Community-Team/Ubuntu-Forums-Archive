---
title: "Locate the daemon ehich sends email"
date: 2012-12-04
forum: General Help
---

### Post by shorn1986 on 2012-12-04
I need to diagnose some faulty mails in an Ubuntu server .

I can see the send mail history from the mail logs . Is there a way to know which daemons send this mails.

---

### Post by Habitual on 2012-12-04
[QUOTE=]I need to diagnose some faulty mails in an Ubuntu server .

I can see the send mail history from the mail logs . Is there a way to know which daemons send this mails.[/QUOTE]

```
sudo grep mail /var/log/mail.log 
```shows here:
```
Dec  4 07:45:01 mysql12 postfix/local[2438]: 
```So this host uses postfix.
The log tells you which is sending the emails.

```
man -k mail
``` will show you the man pages for all installed mail handler packages.

This may help.
[https://help.ubuntu.com/12.04/installation-guide/powerpc/mail-setup.html](https://help.ubuntu.com/12.04/installation-guide/powerpc/mail-setup.html)

---

