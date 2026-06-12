---
title: "[SOLVED] Evolution Error with address (exchange)"
date: 2007-12-04
forum: General Help
---

### Post by jken146 on 2007-12-04
When I try to send an email with my Exchange address, I get this error message: > Error while performing operation.

Your account does not have permission to use <address hidden>
as a From address.

Now this is a Microsoft Exchange account, and I am able to send mail with a POP account that I also have set up in Evolution.  Therefore I guess it's an exchange problem.

Furthermore, this exchange account has been functioning with evolution for months now with no problems, and I didn't change anything or update Evolution recently, so I am inclined to suspect something on the server end has changed.

I have no idea how to fix this.  I have tried deleting ~/.evolution/exchange, but to no avail.

---

### Post by jken146 on 2007-12-05
I created another user and replicated my exchange account setup in evolution there.  It worked fine.  This is confusing me because I tried deleting ~/.evolution in my original user, which didn't solve the problem.  I thought that's where all the configuration stuff lived.

---

### Post by jken146 on 2007-12-06
I deleted the account in Evolution and added it again from scratch.  That did the trick.  Still no idea what was going wrong.

---

