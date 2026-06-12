---
title: "How to setup a email account for a user"
date: 2006-08-27
forum: General Help
---

### Post by chrisdee on 2006-08-27
Hello. I have installed squirrel webmail, postfix and fetchmail
and everything works fine.

Iv setup an useraccount called david hansen, and manage to send and recive webmail through squirrel between the david hansen account and my standard emailaccount. The problem is that in the from field in the email it says "David Hansen" <92@mydomain.selfip.net>. Its supposed to be "David Hansen" <David.Hansen@mydomain.net>

This means I cant reply to the David Hansen account.

What have I done wrong, and how can I solve this ?

I have a rounter wich enables Dynamic DNS from [www.dyndns.com](www.dyndns.com)
and have mydomain.net domain from NetworkSolutions.com. Is the problem on my Ubuntu server or somewhere else ?

---

### Post by chrisdee on 2006-08-28
Anyone ?

---

### Post by chrisdee on 2006-08-28
Maby somebody has a link to a site wich has a manual on this ?

---

### Post by cptnapalm on 2006-08-28
so it does this: domainname.ipaddress.net?

I'm not on my computer at the moment, but I'll see what I can remember off of the top of my head.

When postfix was installed, did you set it up as local, internet, internet smart, none?  If you can't remember, then dpkg-reconfigure will start the setup dialogue.  (*IF* I remember correctly, the smart internet option will then set it up for local and remote.  I *think*.)

The configuration file for postfix is in /etc/postfix.  Unless things have changed wildly, the config file is very easy to understand, for most things.

---

