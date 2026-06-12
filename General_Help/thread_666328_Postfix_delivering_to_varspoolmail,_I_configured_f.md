---
title: "Postfix delivering to /var/spool/mail, I configured for Maildir.. what's wrong?"
date: 2008-01-13
forum: General Help
---

### Post by scottlindner on 2008-01-13
I have Postfix configured to deliver to user's Maildir following all of the configuration pages on the Ubuntu website.  I've done this for Dovecot as well.  I have rechecked so many times I believe I'm clinicly insane.  Postfix is still delivering to /var/spool/mail.

Here's what I have in main.cf:
home_mailbox = Maildir/

What am I doing wrong?

Cheers,
Scott

---

### Post by kkovach on 2008-05-21
I just installed postfix this morning and am seeing the same behavior.  I would be interested in knowing if you or anyone else has an answer to this situation?  Thanks.

---

### Post by tageiru on 2008-07-07
Unsetting mailbox_command solved this problem for me.
```
sudo postconf -e 'mailbox_command ='
```

---

### Post by jmirick on 2008-07-09
IN my case, I have an existing Postfix server doing mbox / pop3, no problems.  I want to shift to maildir / imap so I created another server on another box.  I can send out, but can't receive.  Doesn't bounce, messages sent to it seem to go nowhere.  I'd be happy if it stored the messages ANYWHERE.

---

