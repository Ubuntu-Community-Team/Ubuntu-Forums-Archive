---
title: "Configuring a host to receive email"
date: 2017-07-13
forum: General Help
---

### Post by totalmassretain on 2017-07-13
At work, we have FreeBSD servers that our senior admin has configured to receive email. This is very handy as it allows various services to send an email to the host with an alias specified in /etc/aliases which, in turn, can be piped to a script. For example, if I email 'myalias@myhost.example.com' which has the line 'myalias : "| /path/to/my/script"' in /etc/aliases, then the contents of that email get processed by 'myscript'.

Said senior tech is on vacation for a while and I need to replicate this setup on an Ubuntu server. I've hit the Google but I guess my Google-fu is lacking as I haven't been able to find anything that specifically addresses this need on this platform.

Does anyone have this working or can point me in the right direction?

thanks,

---

### Post by TheFu on 2017-07-13
For internal email, just install postfix (MTA) and procmail.

For internet connected email, things are much more complex due to spam-fighting efforts. The protocols are exactly the same, but the anti-spam stuff adds about 10 more hoops that email has to clear.

---

