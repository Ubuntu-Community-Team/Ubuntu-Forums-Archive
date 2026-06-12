---
title: "simple pop3 server setup"
date: 2008-04-10
forum: General Help
---

### Post by discorsage on 2008-04-10
What I would like to do is get mail for a few accounts into gmail.

The mail is being stored in /var/mail/username

I think pop3 is suitable for this?  I would like to use SSL.  Is there a simple solution for this?  I just tried courrier-pop-ssl.  I telnet'd to port 110 locally to check things out, sent a username and password, and it said "-ERR chdir Maildir failed".  Two things - I don't want to use Maildir style mailboxes.  Does this mean non-SSL pop3 is enabled?

This server will not be receiving mail from the outside nor sending email out from any of these addresses, this is purely so I can store administrative emails in gmail.  I like gmail's interface and search capabilities.

---

