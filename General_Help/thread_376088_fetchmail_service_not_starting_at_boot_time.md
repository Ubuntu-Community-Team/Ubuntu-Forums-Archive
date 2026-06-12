---
title: "fetchmail service not starting at boot time"
date: 2007-03-04
forum: General Help
---

### Post by richieeee on 2007-03-04
Hi

I'm looking to download my emails with fetchmail and noticed that there is a Services app

System -> Administration -> Services

I have fetchmail installed, my fetchmailrc in /etc and it is ticked in the Services app, yet fetchmail does not start at boot time. I expected it to start in daemon mode, but it is not running.

So I'm now looking to add this 

fetchmail -d 600 -f /etc/fetchmailrc -a -L /var/log/fetchmail.log

as an init script, but before I do, I wanted to understand what this Services app should be doing, in case of conflict.

Am I okay to just create my own fetchmail init script and configure with boot-up? I'm running Edgy 6.10

Cheers
Rich

---

### Post by richieeee on 2007-03-04
Figured it out, I needed to change the setting in /etc/default/fetchmail

---

