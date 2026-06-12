---
title: "Figuring out what is trying to send mail"
date: 2023-06-06
forum: General Help
---

### Post by sniper8752 on 2023-06-06
In my syslog file, I have entries where something is trying to send mail via smtp/postfix, and fails, and keeps trying.  How do I find out what is doing this?

---

### Post by TheFu on 2023-06-06
I'd read the logs.  Do you have an MTA setup?  What address is it trying to send at?  You can redirect that address to your userid, then the email headers will likely contain the "FROM" that states the program trying to send.

Also, at/batch/cron will put messages into the queue for delivery automatically.  Those messages clearly say "cron" in them.

If you suspect something nefarious, you'll want to use lsof to see which process is trying to put something into the MTA queue.  The timing for this is very difficult, which is why all my systems have MTA configured to only send emails for specific domains under my control, except the real email server which can send email to any valid address in the world.

BTW, the mail.log file should contain all the information for inbound and outbound SMTP that the MTA touches.

---

