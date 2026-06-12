---
title: "Email: Download and Forward"
date: 2007-08-31
forum: General Help
---

### Post by krbrowning on 2007-08-31
My college recently decided to ban redirecting email on its exchange server.
I need an easy to implement or well documented way to download email from my university account and forward it to my Gmail account.

I know that this is made more difficult because Gmail doesn’t support IMAP.

I’ve tried creating a filter in Evolution, but I don’t see an option to automatically forward email. I’ve played around with fetchmail, but the documentation is a nightmare for average user. 

Something that would run as a daemon is preferable, but at this point I’m looking for anything that works.

---

### Post by kidders on 2007-09-01
Hi there,

> **krbrowning said:**
> I know that this is made more difficult because Gmail doesn&#8217;t support IMAP.I'm not sure how having IMAP support would make any difference. :confused:

Personally, I would opt for a fetchmail/procmail combination. Both apps do take a little getting used to, but they are a standard approach to this type of problem. Others involve doing things like running local SMTP servers, and probably aren't appropriate.

Essentially, fetchmail could retrieve messages from a list of sources, and pipe them to procmail, which is an extremely flexible mail processing utility. To daemonise and automate the process, you could create a fetchmail cron job.

---

### Post by wislon on 2007-09-06
I posted a basic howto 

[http://ubuntuforums.org/showthread.php?t=395522](http://ubuntuforums.org/showthread.php?t=395522)

(see page 2, post #14, hopefully this may help get you started?)

good luck! :)

---

