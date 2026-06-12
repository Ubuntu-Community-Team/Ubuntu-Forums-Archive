---
title: "Firewall and start up issues"
date: 2008-06-08
forum: General Help
---

### Post by Tom--d on 2008-06-08
When I do not use the usplash, it shows all the writing. 

How do I see that writing in the terminal onced logged in?


Well, the firewall problem is.. when I see the writing. Starting basic network. There are a lot of errors with Firestarter.

I can explain when I post the text which was displayed as I cant remember what it said (was too fast for me to read)

So I need the text and then I can explain what I need help with.

Thanks, 
Tom

Also, dmesg doesnt show anything relevant to what I need help with

---

### Post by HalPomeranz on 2008-06-08
Error messages you see on the console at boot time will usually end up in /var/log/syslog.  You could also look in /var/log/daemon.log and /var/log/kern.log.

---

