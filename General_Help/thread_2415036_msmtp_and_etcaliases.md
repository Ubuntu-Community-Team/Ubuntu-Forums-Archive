---
title: "msmtp and /etc/aliases"
date: 2019-03-19
forum: General Help
---

### Post by makke on 2019-03-19
Hi,

I'm running Ubuntu server 18.04 and have configured msmtp to send email alerts from cron jobs to my external email, that works like a charm, but when i run "echo test | mail -s "test message" root" it ignores what I have in my /etc/aliases and tries to send to root@hostname.

What can I have missed?

/etc/msmtprc includes aliases /etc/aliases

and aliases /etc/aliases do have 
root: [email]myemail@domain.com[/email]

Please let me know if I missed any information needed.

Best Regards,
Makke

---

### Post by makke on 2019-03-19
Got it working, was the line postmaster: root in /etc/aliases that was the problem, changing this to my own address instead of "root" did the trick.

---

