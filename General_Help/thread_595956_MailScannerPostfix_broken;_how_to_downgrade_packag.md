---
title: "MailScanner/Postfix broken; how to downgrade package?"
date: 2007-10-29
forum: General Help
---

### Post by remery on 2007-10-29
I upgraded my 6.06LTS install yesterday (sudo aptitude dist-upgrade), which upgraded postfix. According to my logs, it upgraded postfix 2.2.10-1ubuntu0.1 to 2.4.5-3build1~dapper1.

Since the upgrade, mailscanner no longer functions. Every time it runs, a message is logged that postfix didn't exit cleanly, but postfix runs fine on its own. With debugging, mailscanner errors with "Can't call method "DropFromBatch" on unblessed reference at /usr/share/MailScanner/MailScanner/Postfix.pm line 332". I can work with the mailscanner people to figure out the problem and fix it, but I'm not receiving any email in the interim (which makes it hard to work with the mailscanner people :).

My question is, how can I downgrade postfix to the previous version so I can get email until I figure out the problem?

Thanks,
Rick

---

### Post by kc5goi on 2007-12-24
Rick, I am in the same boat.  What I found was that mail is not getting picked up from my HOLD queue.  It is as if MailScanner has decided to ignore it.  I asked around the MailScanner forum and they suggested upgrading to the latest version and another about hash files being an issue around 2.2.*.  I disabled the header check that sends mail to hold but that makes me very nervous.  No AV or spam scanning right now.  My users have noticed the spam increase.  Is the current Debian on mailscanner.info but there are dependancy issues.  A reinstall did not help.  I see the processes start but never scan.

Guy

---

