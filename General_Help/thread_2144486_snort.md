---
title: "snort"
date: 2013-05-12
forum: General Help
---

### Post by eawz9999 on 2013-05-12
I know this has a simple solution but I cannot find it.
My server sends me emails after crontab jobs.
I have Snort update files everyday however I do not receive these messages, [EMAIL="snort@gmail.com"]snort@gmail.com[/EMAIL] IS NOT a user of Gmail and his requests are denied. How do I tell Snort to mail them under [EMAIL="myname@gmail.com"]myname@gmail.com[/EMAIL]?
Now I put [EMAIL="snort@gmail.com"]snort@gmail.com[/EMAIL] as [EMAIL="myname@gmail.com"]myname@gmail.com[/EMAIL] on /etc/aliases. Is this enough?
Thank you,
Enrique

---

### Post by eawz9999 on 2013-05-16
It was, after all, a very simple problem. When Oinkmaster is installed it creates a Crontab under u-snort (which I has forgotten). A simple redirection there solves this issue.

---

