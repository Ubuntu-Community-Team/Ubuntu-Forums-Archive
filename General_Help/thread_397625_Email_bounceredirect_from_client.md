---
title: "Email bounce/redirect from client"
date: 2007-03-30
forum: General Help
---

### Post by spin2cool on 2007-03-30
I'd like to forward a copy of all incoming emails from an IMAP account to my Gmail account for backup purposes.  The catch is, I'd like to maintain the original sender's email address and such.

There is an extension for thunderbird called mailredirect which does exactly this, (it 'bounces' the email) but it only works manually.  I have to select the messages and manually tell it to redirect them - it doesn't integrate with the thunderbird filters.  I would like a solution that will do this automatically for all incoming messages.

My question is, is there a way to do this automatically from thunderbird (or another email client).  For example, I know that Apple Mail has this functionality built in. (as described [in this post]("http://www.boingboing.net/2005/10/13/archiving_email_on_g.html")).  It's an IMAP exchange server at work, so I can't setup a server-side rule to forward email, so it has to be something that I can do on the client side

Does Evolution have this functionality?  Is there another tool like pine or mutt that can do this easily?

---

### Post by spin2cool on 2007-03-30
I found out that running fetchmail will do the trick.  I just set it up to poll the IMAP server every ten minutes, then forward any new mail to my gmail account.  In case anyone else has this problem, here are the parameters I used:

in ~/.fetchmailrc:
```
poll <yourIMAPserverAddress> proto IMAP user "<yourUserName>" with password "<yourPassword>" is "<ubuntuUserName>" here keep options folder Inbox
```

then I run it with:
 fetchmail -v --smtphost <yourSmtpServer> --smtpname <username>@gmail.com -d 600

The only drawback is that it keeps the time that the email was forwarded instead of the time it was sent, but since I'm polling every 10 minutes, it'll be close enough.

Hopefully this helps someone else!!

---

