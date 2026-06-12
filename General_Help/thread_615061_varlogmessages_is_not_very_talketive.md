---
title: "/var/log/messages is not very talketive"
date: 2007-11-16
forum: General Help
---

### Post by kaurman on 2007-11-16
Hi!

I have a problem: /var/log/messages contains very little information and I'm quite sure it's not normal as I remember that there used to be a lot more information in this file earlier. 

Now I basicly only have something about network and then MARK lines:D

It is likely that I've reduced the logging (don't ask which file I changed :)) as I had problems with constant HD access but now I'd like to know how to make /var/log/messages fill with data again.

Or am I wrong and it's perfectly normal that /var/log/messages contains little information?

In that case I just wonder what was the name of the file I used to use to track system problems....

All the best,

Kaur

---

### Post by scorp123 on 2007-11-16
> **kaurman said:**
> I have a problem: /var/log/messages contains very little information  On Ubuntu they split the logs up ... so depending on what info you are looking for, you'd have to take a look at the other log files too, e.g.
[B]/var/log/acpid
/var/log/auth.log
/var/log/boot
/var/log/dmesg
/var/log/syslog[/B]
...

I hope this was helpful.

---

### Post by kaurman on 2007-11-16
> **scorp123 said:**
> On Ubuntu they split the logs up ... so depending on what info you are looking for, you'd have to take a look at the other log files too, e.g.


Thank you for your reply. I know that logs are split up but am particularly interested in /var/log/messages and what it should or should not log by default.

With best wishes,

Kaur

---

### Post by scorp123 on 2007-11-16
> **kaurman said:**
>  but am particularly interested in /var/log/messages and what it should or should not log by default.  That depends on the config file which you can change if you want or need to. Take a look at **/etc/syslog.conf** ...

---

