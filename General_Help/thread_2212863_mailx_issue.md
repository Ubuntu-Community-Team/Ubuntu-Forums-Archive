---
title: "mailx issue"
date: 2014-03-23
forum: General Help
---

### Post by Elastic_Potential on 2014-03-23
I'm trying to get heirloom-mailx to send an email to my phone carrier's text-email address (phonenumber@vtext.com).  For whatever reason, it refuses to.  My friend, however, is able to, and have no idea why.

Can anyone hazard to guess why?

---

### Post by Elastic_Potential on 2014-03-23
Found this error in /var/log/mail.log:
```
Mar 23 17:18:41 Sera postfix/smtp[22293]: CA64A181B48: to=<phonenumber@vtext.com>, relay=smtp-bb.vtext.com[69.78.128.213]:25, delay=1.9, delays=0.1/0/1.8/0, dsn=4.0.0, status=deferred (host smtp-bb.vtext.com[69.78.128.213] refused to talk to me: 554 njbrspamp3.vtext.com)
```
It looks like Verizon is refusing my messages.  Is there really anything else that I can do from this point?

---

### Post by Habitual on 2014-03-24
Contact Verizon?

---

