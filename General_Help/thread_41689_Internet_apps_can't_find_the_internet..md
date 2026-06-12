---
title: "Internet apps can't find the internet."
date: 2005-06-14
forum: General Help
---

### Post by fivre on 2005-06-14
Not sure if this is the right forum, may go in Networking, but it seemed to be a software-side problem.

Anyway, after much pain and hardship, I discovered the elusive reason I couldn't connect to the internet. (My ISP is a bit iffy on giving out passwords and usernames to users.) Now, it seems, I am connected. The terminal isn't displaying the Modem Hangup(SIGHUP) message, the modem's "Connection Established/Data Transfer Active" lights are on, and the phone line makes that annoying noise.

Unfortunately, neither Firefox nor X-chat seem to be aware of this, and are puttering on as if there was no connection at all. This is very frustrating. Any ideas on how to fix it?

---

### Post by desdinova on 2005-06-14
try putting your isp's dns servers in /etc/resolv.conf

---

