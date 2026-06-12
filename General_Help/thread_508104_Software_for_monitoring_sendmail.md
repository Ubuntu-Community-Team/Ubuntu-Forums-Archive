---
title: "Software for monitoring sendmail?"
date: 2007-07-23
forum: General Help
---

### Post by Beefeater on 2007-07-23
Hi,

I'm looking for software to monitor sendmail.
Number of emails, who sent it etc.

Any ideas?

Cheers

---

### Post by Mr. C. on 2007-07-23
[http://www.logwatch.org](http://www.logwatch.org)

MrC

---

### Post by Beefeater on 2007-07-23
> **Mr. C. said:**
> [http://www.logwatch.org](http://www.logwatch.org)

MrC

Thanks for your reply.
I've used logwatch before but it only gives you Number of sent emails.
Guess it will have to do for now if there isn't a way to configure logwatch to see who you sent the email to.

---

### Post by Mr. C. on 2007-07-23
The sendmail filter has been updated several times recently.  You get more detail with detail level 10, as in :

```
logwatch --detail 10 --service sendmail
```

Be sure to get the latest version of logwatch if you haven't used it in a while.

I use postfix, and wrote the postfix logwatch filter and utility, which gives as much info as you ask.

[http://www.mikecappella.com/logwatch](http://www.mikecappella.com/logwatch)

MrC

---

