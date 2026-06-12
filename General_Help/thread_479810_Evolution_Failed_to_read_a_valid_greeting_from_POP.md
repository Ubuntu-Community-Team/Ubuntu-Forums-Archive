---
title: "Evolution: Failed to read a valid greeting from POP server"
date: 2007-06-20
forum: General Help
---

### Post by Enigmatic on 2007-06-20
I'm wondering how I can fix this error.

I get it while Evolution syncs with my mail server running Postfix. I have a few domains on there and about 2-3 addresses per.

It seems to happen with just the one domain, but mail downloads just fine. 

So it's something that's more of an annoyance than something broken, but I'd like it fixed just the same. :p

---

### Post by oomingmak on 2007-07-12
I have the same problem.

Every time I open Evolution I get that error. But if I wait a few minutes then I can usually do a send and received with no problems.

But on each first opening, that error message comes up.

---

### Post by tog_benson on 2007-10-18
I am also having this problem.  I don't have it with four accounts, but I do with five.

---

### Post by tog_benson on 2007-10-21
EDIT:  this didn't fix it.  Evolution sucks my balls.



OK, this made it go away for me.

I used to have 5 email accounts on 4 domains.  The mail server in my preferences was the same for all 5.

[email]emaila@domain1.com[/email] (mail server) mail.server.com
[email]emailb@domain2.com[/email] (mail server) mail.server.com
[email]emailc@domain3.com[/email] (mail server) mail.server.com
[email]emaild@domain3.com[/email] (mail server) mail.server.com
[email]emaile@domain4.com[/email] (mail server) mail.server.com

It seems evolution craps out when all 5 accounts are configured on the same mail server.  So I changed the5 accounts to use the mail.domain.com for their respective domains.

[email]emaila@domain1.com[/email] (mail server) mail.domain1.com
[email]emailb@domain2.com[/email] (mail server) mail.domain2.com
[email]emailc@domain3.com[/email] (mail server) mail.domain3.com
[email]emaild@domain3.com[/email] (mail server) mail.domain3.com
[email]emaile@domain4.com[/email] (mail server) mail.domain4.com

The dns for all the above mail servers still points to the same mail server.  Then the error goes away.

Someone at evolution needs to fix this. Geez.

---

### Post by tog_benson on 2007-10-23
Well, for now reducing the frequency which I check mail has helped.  Some accounts I set to every 2 or 3 minutes instead of once per minute.

---

### Post by unclecameron on 2008-03-25
I have DNS entries for 

domain1.com
domain2.com
domain3.com
domain4.com

(and 4 more) that all point to the same mailserver/IP running virtual hosts, and I get this message every time I launch the app, but not after that.

I also have an Exchange account sync'ing up, and it occasionally loses sync, but works otherwise.

---

### Post by frogotronic on 2008-05-16
I also have this problem, but just have one account.

Any thoughts on how to get rid of this annoyance?

---

### Post by unclecameron on 2008-05-16
I couldn't resolve this issue, so I upgraded far ahead of the Hardy release, and with the new version of Evolution the error doesn't pop up irritatingly, it just stays as a warning box in the bottom status bar on the application, it still happens though.

---

