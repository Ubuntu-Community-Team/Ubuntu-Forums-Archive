---
title: "Evolution error on startup"
date: 2005-08-04
forum: General Help
---

### Post by mmrobins on 2005-08-04
Almost every time I try to start Evolution, which I have configured to get mail from my Microsoft Exchange 2000 server, I get the following error:

The Application "evolution-exchange-storage" has quit unexpectedly.

Every so often this won't happen and it will just startup and be able to read my exchange e-mail.  I found this hint that is a workaround to get it working every time: [http://lists.ximian.com/pipermail/evolution/2005-March/042424.html](http://lists.ximian.com/pipermail/evolution/2005-March/042424.html)
When I run E2K_DEBUG=4 /usr/lib/evolution/2.2/evolution-exchange-storage I get the following output:

(evolution-exchange-storage:7763): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Evolution Exchange Storage up and running
E2K_DEBUG=4

Then if I run Evolution it starts up fine every time.

I found that other people are having the same problem, here [http://ubuntuforums.org/archive/index.php/t-12755.html](http://ubuntuforums.org/archive/index.php/t-12755.html) for example, but I haven't seen a reason for this happening.

Does anyone else know what might be going on or where I could look for a fix? Thanks.

---

