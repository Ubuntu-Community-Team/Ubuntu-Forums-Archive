---
title: "Procmail recipe question"
date: 2013-04-15
forum: General Help
---

### Post by silentcreek on 2013-04-15
Hi everybody,

the following question is rather procmail-specific than Ubuntu-specific, but I hope somebody here is able to help me. 

I'm trying to set up a procmail filter that does the following: Filter all email coming from a specific email address and do two actions: 1) Send an automated reply to the email-address in the reply-to field*, and 2) copy the email to the Inbox.
*Note all emails coming from that "specific" email address have a Reply-to field set with an email address that is different from the "From" address.

I have two problems with that recipe in particular: I don't understand the syntax to send an email to the email address contained in the reply-to field of the original email address. Plus, somehow my second action is never executed.

```
:0: H h c
* ^From:.*(specific@emailadress.com)
# here should be the action to send an automated reply to the address contained in the reply-to field of the mail header
:0:
$HOME/mail/Inbox
# Note: the second action is never executed regardless of the first action... Something is wrong here...
```

Could anybody explain the proper systax for my purpose to me?

Thanks! And sorry for my ignorance. I tried to help myself reading documentations and man-pages, but couldn't figure out anything that worked.

---

