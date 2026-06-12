---
title: "Printer instalation in Gutsy"
date: 2007-10-17
forum: General Help
---

### Post by prunesquallor on 2007-10-17
Trying to setup of a Lexmark C532dn laser colour printer via  Administration-Printing. I have the ppd file, but I get asked for my password which it does not recognise (probably the CUPS password).

I read a post that guided users on adding cupsys to the shadow group by enabling “Show all users” and/or “Show all groups” in the Users and Groups utility. However, in Gutsy there is no such option.

So, my question is - how can I get/change the CUPS password?

---

### Post by 505 on 2007-10-17
It can also be that the CUPS service it not running. Try this in a terminal first:
```
sudo /etc/init.d/cupsys restart
```

---

### Post by prunesquallor on 2007-10-17
Thanks for your reply.

CUPS was already running, but I restarted it anyway as per your instruction. But it still refuses to recognise my password.

---

### Post by sgornick on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: 152061 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See Bug #152061
Can you try:
  $ gksudo system-config-printer

---

### Post by prunesquallor on 2007-10-20
That worked. Many thanks.

---

### Post by ionospheric on 2007-10-20
It worked for me too, thanks so much.

Apparently, the problem occurs when a user other than the first one created uses CUPS.

---

