---
title: "email from terminal"
date: 2008-07-02
forum: General Help
---

### Post by pavel989 on 2008-07-02
i have tried using mail and mutt, and the evoltuion mailto:

but 

evolution opens a graphical thing, i just need it to send,

mail and mutt can't send either because mail can't send to external address or mutt says that there are bad messages

the other problem is that i have VZ fios, and ports 25 and 80 are blocked. And i need this for squid to send me email if there are errors (i doubt there will be but who knows). maybe theres a way around this?

---

### Post by soccerboy on 2008-07-02
have you tried sendmail?

---

### Post by pavel989 on 2008-07-02
yea but it doesn't seem to work either. heres another thing:
> #	Email program used to send mail if the cache dies.
#	The default is "mail". The specified program must comply
#	with the standard Unix mail syntax:
#	  mail-program recipient < mailfile

---

### Post by dcstar on 2008-07-03
> **pavel989 said:**
> i have tried using mail and mutt, and the evoltuion mailto:

but 

evolution opens a graphical thing, i just need it to send,

mail and mutt can't send either because mail can't send to external address or mutt says that there are bad messages

the other problem is that i have VZ fios, and ports 25 and 80 are blocked. And i need this for squid to send me email if there are errors (i doubt there will be but who knows). maybe theres a way around this?

You install the **mailx** and **postfix** packages.

---

### Post by justleen on 2008-07-03
go with postfix, as dcstar says.. much easier to config then sendmail....

once that runs, you can use either mailx or mutt (i preffer mutt personally...)

---

### Post by pavel989 on 2008-07-04
ive installed mailx but idk about postfix package, ill check it out

---

