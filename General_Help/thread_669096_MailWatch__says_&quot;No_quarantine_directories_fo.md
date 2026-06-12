---
title: "MailWatch  says &quot;No quarantine directories found&quot;"
date: 2008-01-16
forum: General Help
---

### Post by fychan on 2008-01-16
I posted a week or so ago in the Absolute Beginner Talk section ([http://ubuntuforums.org/showthread.php?t=662719](http://ubuntuforums.org/showthread.php?t=662719)) asking about this problem, but have received no replies.  I really need to get this sorted, so I'm hoping that by reposting in the general section, I might get more responses.  Sorry for the repost...
__________

I've got Ubuntu (Gutsy) up & running as a home server - using Postfix to handle incoming mail, Dovecot to provide an IMAP interface and a combination of MailScanner & spamassassin to try & filter out spam (no anti-virus installed yet, as each client machine is running it's own already it's not a /very/ high priority).

I installed MailWatch the other day, in the hope that it would allow me to re-identify HAM and SPAM that the other programs had mis-diagnosed and it's all up and running nicely - with the last 50 messages showing on the homepage, and the black/white lists running just fine - but when I click on the "Quarantine" link, it lists the top of the tap & options fine then just says:

"No quarantine directories found"

I've used Google a lot trying to solve this issue - and a lot of people seem to get function errors & all sorts in connection with this message. I'm getting no errors (not even in the Apache logs), just a friendly (and uninformative!) message. I've checked all the permissions (as per all the posts I've found) and they're all good. I've gone through the Wiki and made all those changes, I've also run the "fix_quarantine_permissions" script in the MailWatch install directory to no avail.

Has anyone got any ideas at all? I'm at my wits end now...

Cheers

---

