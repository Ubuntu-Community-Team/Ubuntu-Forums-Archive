---
title: "How to set it up so the system uses SMTP by default"
date: 2007-02-25
forum: General Help
---

### Post by CaptSaltyJack on 2007-02-25
There are few apps on Ubuntu that, by default, expect to just send out an email and hope it gets to its destination.  For example, php's mail() function.  These emails are now probably lying around as drafts in some spool directory on my system.

How do I set up my Ubuntu machine so that everything that uses the mail system will actually connect to an SMTP server to deliver the mail?

---

### Post by scxtt on 2007-02-25
do you have "postfix" and/or "sendmail" installed? ... i use postfix myself, and as i try to remember, i was able to get php's mail() function to work ...

---

### Post by CaptSaltyJack on 2007-02-25
I have postfix installed.  sendmail, I just installed.. but I have no clue how to set it up to connect to a specified SMTP server to send mail.

---

### Post by scxtt on 2007-02-25
are you able to do something like:

mailx -s "this is a test." [email]user@email.com[/email] < input.txt

that'll send an email (w/ the contents of input.txt) through postfix w/ "this is a test." as the subject to [email]user@email.com[/email] ...

you might want to install **mailx** as well ...

```
:> aptitude search mailx
i   mailx                                          - A simple mail user agent
```

---

### Post by CaptSaltyJack on 2007-02-25
Oh, that worked.. I uninstalled sendmail & postfix, and just reinstalled postfix.

---

### Post by CaptSaltyJack on 2007-04-16
OK, I have Ubuntu 6.10 server on a machine at work now, and can't get email working.  The Ubuntu box should be connecting to another SMTP server to send its mail off.  How do I configure postfix to work that way??

---

### Post by CaptSaltyJack on 2007-04-17
Anyone?

---

